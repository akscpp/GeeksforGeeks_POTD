[Problem Link](https://www.geeksforgeeks.org/problems/toeplitz-matrix/1)<br>

A Toeplitz (or diagonal-constant) matrix is a matrix in which each descending diagonal from left to right is constant, i.e., all elements in a diagonal are the same. Given a rectangular matrix mat, your task is to complete the function isToeplitz which returns true if the matrix is Toeplitz otherwise, it returns false.<br>

Examples:<br>

Input:<br>
mat = [[6, 7, 8],<br>
       [4, 6, 7],<br>
       [1, 4, 6]]<br>
Output: true<br>
Explanation: The test case represents a 3x3 matrix<br>
 6 7 8 <br>
 4 6 7 <br>
 1 4 6<br>
Output will be true, as values in all downward diagonals from left to right contain the same elements.<br>
Input: <br>
mat = [[1,2,3],<br>
       [4,5,6]]<br>
Output: false<br>
Explanation: Matrix of order 2x3 will be 1 2 3 4 5 6 Output: false as values in all diagonals are not the same.<br>
Constraints:<br>
1<=mat.size,mat[0].size<=40<br>
0<=mat[i][j]<=100<br>

Expected time complexity: O(n*m)<br>
Expected space complexity: O(1)<br>

__Intuition ->Traverse the matrix. For each cell (i,j), calculate (i+1,j+1) and if it is within the boundary , check if it same as the value at (i,j).__

```C++
bool isToeplitz(vector<vector<int>>& mat) {
    // code here
    int n = mat.size();
    int m = mat[0].size();
    
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            int nr = i+1;
            int nc = j+1;
            
            if(nr>=0 && nr<n && nc>=0 && nc<m){
                if(mat[nr][nc]!=mat[i][j]){
                    return false;
                }
            }
        }
    }
    
    return true;
}
```
