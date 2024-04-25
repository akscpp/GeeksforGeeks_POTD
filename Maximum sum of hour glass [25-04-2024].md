[Problem Link](https://www.geeksforgeeks.org/problems/maximum-sum-of-hour-glass3842/1)<br>
Given two integers n, m and a 2D matrix mat of dimensions nxm, the task is to find the maximum sum of an hourglass.<br>
An hourglass is defined as a part of the matrix with the following form:<br>



Return -1 if any hourglass is not found.<br>

Example 1:<br>

Input:<br>
n = 3, m = 3<br>
mat = [[1, 2, 3],<br>
       [4, 5, 6],<br>
       [7, 8, 9]]<br>
Output:
35<br>
Explanation:
There is only one hour glass which is<br>
1 2 3<br>
  5<br>
7 8 9   and its sum is 35.<br>
Example 2:<br>

Input:<br>
n = 2, m = 3<br>
mat = [[1, 2, 3],<br>
       [4, 5, 6]]<br>
Output:
-1<br>
Explanation:<br>
There are no hour glasses in this matrix.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function findMaxSum() which takes the two integers n, m, and the 2D matrix mat as input parameters and returns the maximum sum of an hourglass in the matrix. If there are no hourglasses, it returns -1.<br>

Expected Time Complexity: O(n*m)<br>
Expected Auxillary Space: O(1)<br>

Constraints:<br>
1 <= n <= 150<br>
3 <= m <= 150<br>
0 <= mat[i][j] <= 10^6<br>

__Intuition -> For an hour glass to be formed , there must be atleast 3 rows and 3 columns. If less than 3 , return -1. Iterate the matrix till (n-3)th row and (m-3)th column and calculate all the 7 points required to formed an hour glass. Find their sum and take maximum of all those sum.__

```C++
int findMaxSum(int n, int m, vector<vector<int>> mat) {
        // code here
        if(n<3 || m<3) return -1;
        int ans = -1;
        
        for(int i=0;i<n-2;i++){
            int sum=0;
            for(int j =0;j<m-2;j++){
                int A = mat[i][j];
                int B = mat[i][j+1];
                int C = mat[i][j+2];
                int D = mat[i+1][j+1];
                int E = mat[i+2][j];
                int F = mat[i+2][j+1];
                int G = mat[i+2][j+2];
                
                sum = A+B+C+D+E+F+G;
                ans=max(ans,sum);
            }
            
        }
        return ans;
    }
```
