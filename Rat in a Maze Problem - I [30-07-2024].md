[Problem Link](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)<br>

Consider a rat placed at (0, 0) in a square matrix mat of order n* n. It has to reach the destination at (n - 1, n - 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are 'U'(up), 'D'(down), 'L' (left), 'R' (right). Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.<br>
Note: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell. In case of no path, return an empty list. The driver will output "-1" automatically.<br>

![image](https://github.com/user-attachments/assets/6a6b5dcf-52a1-4e34-8096-b72b28027676)


Expected Time Complexity: O(3^n^2)<br>
Expected Auxiliary Space: O(l * x)<br>
Here l = length of the path, x = number of paths.<br>

Constraints:<br>
2 ≤ n ≤ 5<br>
0 ≤ mat[i][j] ≤ 1<br>

__Intuition ->Use recursion to trace every path and include the valid paths in the answer.__

```C++
vector<string> ans;
    void solve(int i, int j, string path, vector<vector<int>> &mat, int n){
        if(i < 0 or i >= n or j < 0 or j >= n or mat[i][j] == 0){
            return;
        }
        if(i == n-1 and j == n-1){
            ans.push_back(path);
            return;
        }
        mat[i][j] = 0;
        
        solve(i-1, j, path + 'U', mat, n);
        solve(i+1, j, path + 'D', mat, n);
        solve(i, j+1, path + 'R', mat, n);
        solve(i, j-1, path + 'L', mat, n);
        
        mat[i][j] = 1;
        
    }
    vector<string> findPath(vector<vector<int>> &mat) {
        int n = mat.size();
        
        string path = "";
        solve(0, 0, path, mat, n);
        return ans;
    }
```
