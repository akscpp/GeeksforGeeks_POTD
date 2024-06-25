[Problem Link](https://www.geeksforgeeks.org/problems/left-rotate-matrix-k-times2351/1)<br>

You are given an integer k and matrix mat. Return a matrix where it is rotated Left k times.<br>

Examples:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/a4f7d6e3-27c3-435f-a0b6-803577e7c98a)<br>

Expected Time Complexity: O(n*m)<br>
Expected Auxillary Space: O(n*m)<br>

Constraints:<br>
1<= mat.size, mat[0].size, mat[i][j] <=1000<br>
1<=k<=10000<br>

__Intuition -> Calculate the effective rotation by taking k modulo the number of columns, initializing a new matrix ans of the same dimensions with all elements set to -1, and iterate through each element of mat, placing each element in its new position (j + k) % m within the corresponding row of ans. Finally,return the rotated matrix ans.__

```C++
vector<vector<int>> rotateMatrix(int k, vector<vector<int>> mat) {
        int n = mat.size();
        int m = mat[0].size();
        
        k = k%m;
        
        vector<vector<int>> ans(n,vector<int>(m,-1));
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                ans[i][j]=(mat[i][(j+k)%m]);
            }
        }
        
        return ans;
    }
```
