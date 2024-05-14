[Problem Link](https://www.geeksforgeeks.org/problems/path-with-minimum-effort/1)<br>
You are a hiker preparing for an upcoming hike. You are given heights[][], a 2D array of size rows x columns, where heights[row][col] represents the height of cell (row, col). You are situated in the top-left cell, (0, 0), and you hope to travel to the bottom-right cell, (rows-1, columns-1) (i.e., 0-indexed). You can move up, down, left, or right, and you wish to find the route with minimum effort.<br>

Note: A route's effort is the maximum absolute difference in heights between two consecutive cells of the route.<br>

Example 1:<br>

Input:<br>
row = 3<br>
columns = 3 <br>
heights = [[1,2,2],[3,8,2],[5,3,5]]<br>
Output: 
2<br>
Explaination: 
The route 1->3->5->3->5 has a maximum absolute difference of 2 in consecutive cells. This is better than the route 1->2->2->2->5, where the maximum absolute difference is 3.<br>
Example 2:<br>

Input:<br>
row = 2<br>
columns = 2 <br>
heights = [[7,7],[7,7]]<br>
Output: 
0<br>
Explaination: <br>
Any route from the top-left cell to the bottom-right cell has a maximum absolute difference of 0 in consecutive cells.<br>
Your Task:
You don't need to read input or print anything. Your task is to complete the function MinimumEffort() which takes intergers rows, columns, and the 2D array heights[][]  and returns the minimum effort required to travel from the top-left cell to the bottom-right cell.<br>

Expected Time Complexity: O(rowsxcolumns)<br>
Expected Space Complexity: O(rowsxcolumns)<br>

Constraints:<br>
1 <= rows, columns <= 100<br>
rows == heights.length<br>
columns == heights[i].length<br>
0 <= heights[i][j] <= 10^6<br>

__Intuition ->The MinimumEffort function efficiently finds the shortest path through a grid with variable heights. It uses BFS to explore adjacent positions, updating the minimum effort required for each step. The vis array tracks these efforts, returning the minimum required to reach the bottom-right corner, or 0 if unreachable.__

```C++
int MinimumEffort(int rows, int columns, vector<vector<int>> &heights) {
        // code here
        queue<pair<int,pair<int,int>>>q;
        
        vector<vector<int>>vis(rows,vector<int>(columns,1e9));
        
        q.push({0,{0,0}});
        
        int delR[]={-1,0,1,0};
        int delC[]={0,-1,0,1};
        
        while(!q.empty()){
            int diff = q.front().first;
            int i = q.front().second.first;
            int j = q.front().second.second;
            
            q.pop();
            
            for(int k=0;k<4;k++){
                int nr = i+delR[k];
                int nc = j+delC[k];
                
                if(nr>=0 && nr<rows && nc>=0 && nc<columns){
                    int newD = max(diff,abs(heights[i][j]-heights[nr][nc]));
                    
                    if(newD<vis[nr][nc]){
                        vis[nr][nc]=newD;
                        q.push({newD,{nr,nc}});
                    }
                }
            }
        }
        return vis[rows-1][columns-1]!=1e9?vis[rows-1][columns-1]:0;
    }
```
