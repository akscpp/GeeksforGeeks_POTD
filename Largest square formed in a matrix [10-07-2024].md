[Problem Link](https://www.geeksforgeeks.org/problems/largest-square-formed-in-a-matrix0806/1)<br>
Given a binary matrix mat of size n * m, find out the maximum length of a side of a square sub-matrix with all 1s.<br>

Examples:<br>

Input: n = 6, m = 5<br>
mat = [[0, 1, 1, 0, 1], <br>
       [1, 1, 0, 1, 0],<br>
       [0, 1, 1, 1, 0],<br>
       [1, 1, 1, 1, 0],<br>
       [1, 1, 1, 1, 1],<br>
       [0, 0, 0, 0, 0]]<br>
Output: 3<br>
Explanation: <br>

The maximum length of a side of the square sub-matrix is 3 where every element is 1.<br>
Input: n = 2, m = 2<br>
mat = [[1, 1], <br>
       [1, 1]]<br>
Output: 2<br>
Explanation: The maximum length of a side of the square sub-matrix is 2. The matrix itself is the maximum sized sub-matrix in this case.<br>
Input: n = 2, m = 2<br>
mat = [[0, 0], <br>
       [0, 0]]<br>
Output: 0<br>
Explanation: There is no 1 in the matrix.<br>
Expected Time Complexity: O(n*m)<br>
Expected Auxiliary Space: O(n*m)<br>

Constraints:<br>
1 ≤ n, m ≤ 500<br>
0 ≤ mat[i][j] ≤ 1<br>

__Intuition ->For every (i,j), check for 3 other points that make a square. If it is square , keep updating the size.__

```C++
int maxSquare(int n, int m, vector<vector<int>> mat) {
        int res = 0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(i-1>=0 && j-1>=0 && mat[i][j]==1){
                    mat[i][j]=min({mat[i-1][j],mat[i][j-1],mat[i-1][j-1]})+1;
                    
                }
                res = max(res,mat[i][j]);
            }
        }
        return res;
    }
```
