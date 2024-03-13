Given a square matrix mat[][] of n*n size, the task is to determine the diagonal pattern which is a linear arrangement of the elements of the matrix as depicted in the following example:<br>



Example 1:<br>

Input:
n = 3<br>
mat[][] = {{1, 2, 3},
           {4, 5, 6},
           {7, 8, 9}}<br>
Output: {1, 2, 4, 7, 5, 3, 6, 8, 9}<br>
Explaination:
Starting from (0, 0): 1,<br>
Move to the right to (0, 1): 2,<br>
Move diagonally down to (1, 0): 4,<br>
Move diagonally down to (2, 0): 7,<br>
Move diagonally up to (1, 1): 5,<br>
Move diagonally up to (0, 2): 3,<br>
Move to the right to (1, 2): 6,<br>
Move diagonally up to (2, 1): 8,<br>
Move diagonally up to (2, 2): 9<br>
There for the output is {1, 2, 4, 7, 5, 3, 6, 8, 9}.<br>
Example 2:<br>

Input:
n = 2<br>
mat[][] = {{1, 2},
           {3, 4}}<br>
Output: {1, 2, 3, 4}<br>
Explaination:<br>
Starting from (0, 0): 1,<br>
Move to the right to (0, 1): 2,<br>
Move diagonally down to (1, 0): 3,<br>
Move to the right to (1, 1): 4<br>
There for the output is {1, 2, 3, 4}.<br>
Your Task:<br>
You only need to implement the given function matrixDiagonally() which takes a matrix mat[][] of size n*n as an input and returns a list of integers containing the matrix diagonally. Do not read input, instead use the arguments given in the function.<br>

Expected Time Complexity: O(n*n).<br>
Expected Auxiliary Space: O(1).<br>
Constraints:
1 <= n <= 100<br>
-100 <= elements of matrix <= 100<br>


__Intuition -> Traverse the matrix diagonally upwards and diagonally downwards alternatively and keep updating row and column.__

```C++
vector<int> matrixDiagonally(vector<vector<int>>&mat)
    {
         vector<int> ans;
         int row=0,col=0;
         int n = mat.size();
         
         while(ans.size()<=n*n){
             
             //going upward diagonal
             
             while(row>=0 && col<n){
                 if(row>=0 && row<n && col>=0 && col<n){
                     ans.push_back(mat[row][col]);
                     mat[row][col]=1e9;
                 }
                 row--;
                 col++;
             }
             if(ans.size()==n*n){
                 break;
             }

             row = max(row,0);
             col = min(col,n-1);
             
             while(mat[row][col]==1e9){
                 row++;
             }
             
             
             
             //going downward diagonal
             
             while(col>=0 && row<n){
                 if(row>=0 && row<n && col>=0 && col<n){
                     ans.push_back(mat[row][col]);
                     mat[row][col]=1e9;
                 }
                 col--;
                 row++;
             }
             if(ans.size()==n*n){
                 break;
             }

             row = min(row,n-1);
             col = max(col,0);
             
             while(mat[row][col]==1e9){
                 col++;
             }
             
         }
         return ans;
    }
```
