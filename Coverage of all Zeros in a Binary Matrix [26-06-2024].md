[Problem Link](https://www.geeksforgeeks.org/problems/coverage-of-all-zeros-in-a-binary-matrix4024/1)<br>

Given a binary matrix contains 0s and 1s only, we need to find the sum of coverage of all zeros of the matrix where coverage for a particular 0 is defined as a total number of ones around a zero in left, right, up and bottom directions.<br>

Examples:<br>

Input:<br>
matrix = [[0, 1, 0],<br>
          [0, 1, 1],<br>
          [0, 0, 0]]<br>
Output: 6<br>
Explanation: There are a total of 6 coverage are there<br>

Input: <br>
matrix = [[0, 1]]<br>
Output: 1<br>
Explanation: There are only 1 coverage.<br>
Expected Time Complexity: O(n * m)<br>
Expected Space Complexity: O(1)<br>

Constraints:<br>
1 <= matrix.size, matrix[0].size <= 100<br>

__Intuition ->Traverse the matrix and keep checking the surrounding 4 directions.__

```C++
int findCoverage(vector<vector<int>>& mat) {
        // Code here
        int delR[]={-1,0,1,0};
        int delC[]={0,-1,0,1};
        int cnt=0;
        int n = mat.size();
        int m = mat[0].size();
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(mat[i][j]==1) continue;
                
                for(int k=0;k<4;k++){
                    int row = i+delR[k];
                    int col = j+delC[k];
                    if(row>=0 && row<n && col>=0 && col<m && mat[row][col]==1){
                        cnt++;
                    }
                }
            }
        }
        return cnt;
    }
```
