[Problem Link](https://www.geeksforgeeks.org/problems/maximum-connected-group/1)<br>

You are given a square binary grid. A grid is considered binary if every value in the grid is either 1 or 0. You can change at most one cell in the grid from 0 to 1. You need to find the largest group of connected  1's. Two cells are said to be connected if both are adjacent(top, bottom, left, right) to each other and both have the same value.<br>

Examples :<br>

Input: grid = [1, 1]<br>
             [0, 1]<br>
Output: 4<br>
Explanation: By changing cell (2,1), we can obtain a connected group of 4 1's<br>
[1, 1]<br>
[1, 1]<br>
Input: grid = [1, 0, 1]<br>
             [1, 0, 1]<br>
             [1, 0, 1]<br>
Output: 7<br>
Explanation: By changing cell (3,2), we can obtain a connected group of 7 1's<br>
[1, 0, 1]<br>
[1, 0, 1]<br>
[1, 1, 1]<br>
Expected Time Complexity: O(n^2)
Expected Auxiliary Space: O(n^2)

Constraints:<br>
1 <= size of the grid<= 500<br>
0 <= grid[i][j] <= 1<br>

__Intuition ->The MaxConnection function determines the maximum possible size of a connected component in a binary grid after changing one 0 to 1. It uses depth-first search (DFS) to identify and label all connected components of 1s, recording their sizes. The function then examines each 0 cell, calculating the potential size of a new component formed by changing that 0 to 1 and connecting adjacent components. The maximum component size, either from these potential new components or the existing ones, is returned.__

```C++
int MaxConnection(vector<vector<int>>& grid) {
        int n = grid.size();
        if (n == 0) return 0;
        vector<vector<bool>> visited(n, vector<bool>(n, false));
        vector<vector<int>> componentSize(n, vector<int>(n, 0));
        int componentId = 2; 
        unordered_map<int, int> sizeMap;

        function<int(int, int, int)> dfs = [&](int x, int y, int id) {
            if (x < 0 || y < 0 || x >= n || y >= n || visited[x][y] || grid[x][y] == 0)
                return 0;
            visited[x][y] = true;
            componentSize[x][y] = id;
            int size = 1;
            size += dfs(x + 1, y, id);
            size += dfs(x - 1, y, id);
            size += dfs(x, y + 1, id);
            size += dfs(x, y - 1, id);
            return size;
        };

        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] == 1 && !visited[i][j]) {
                    int size = dfs(i, j, componentId);
                    sizeMap[componentId] = size;
                    ++componentId;
                }
            }
        }

        int maxConnected = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] == 0) {
                    unordered_map<int, int> neighborComponents;
                    if (i > 0 && grid[i - 1][j] == 1) neighborComponents[componentSize[i - 1][j]]++;
                    if (i < n - 1 && grid[i + 1][j] == 1) neighborComponents[componentSize[i + 1][j]]++;
                    if (j > 0 && grid[i][j - 1] == 1) neighborComponents[componentSize[i][j - 1]]++;
                    if (j < n - 1 && grid[i][j + 1] == 1) neighborComponents[componentSize[i][j + 1]]++;

                    int potentialSize = 1; // changing this 0 to 1
                    for (auto& kv : neighborComponents) {
                        potentialSize += sizeMap[kv.first];
                    }
                    maxConnected = max(maxConnected, potentialSize);
                }
            }
        }

        for (auto& kv : sizeMap) {
            maxConnected = max(maxConnected, kv.second);
        }

        return maxConnected;
    }
```
