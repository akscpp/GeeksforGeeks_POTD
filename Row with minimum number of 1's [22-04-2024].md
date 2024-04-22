[Problem Link](https://www.geeksforgeeks.org/problems/row-with-minimum-number-of-1s5430/1)<br>
Given a 2D binary matrix(1-based indexed) a of dimensions nxm , determine the row that contains the minimum number of 1's.<br>
Note: The matrix contains only 1's and 0's. Also, if two or more rows contain the minimum number of 1's, the answer is the lowest of those indices.<br>

Example 1:<br>

Input:<br>
n = 4,m = 4<br>
a = [[1, 1, 1, 1],<br>
     [1, 1, 0, 0],<br>
     [0, 0, 1, 1],<br>
     [1, 1, 1, 1]]<br>
Output:
2<br>
Explanation:
Rows 2 and 3 contain the minimum number 
of 1's(2 each).Since,row 2 is less than row 3.
Thus, the answer is 2.<br>
Example 2:<br>

Input:<br>
n = 3,m = 3<br>
a = [[0, 0, 0],<br>
     [0, 0, 0],<br>
     [0, 0, 0]]<br>
Output:
1<br>
Explanation:
All the rows contain the same number 
of 1's(0 each).Among them, index 1 
is the smallest, so the answer is 1.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function minRow() which takes the two integers n, m as well as the 2D binary matrix a as input parameters and returns the minimum index of the row which contains the least number of 1's.<br>

Expected Time Complexity:O(n*m)<br>
Expected Auxillary Space:O(1)<br>

Constraints:<br>
1 <= n,m <= 1000<br>

0 <= a[i][j] <= 1<br>

__Intuition -> Traverse the matrix and count number of 1's in each row. Then compare and store minimum.__

```C++
int minRow(int n, int m, vector<vector<int>> a) {
        // code here
        int min_idx = 1e9;
        int cnt=0;
        int res = 1e9;
        
        for(int i=0;i<n;i++){
            cnt=0;
            for(int j=0;j<m;j++){
                if(a[i][j]==1){
                    cnt++;
                }
            }
            if(cnt<res){
                min_idx = i;
                res = cnt;
            }
        }
        return min_idx+1;
    }
```
