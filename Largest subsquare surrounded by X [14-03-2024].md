Given a square matrix a of size n x n, where each cell can be either 'X' or 'O', you need to find the size of the largest square subgrid that is completely surrounded by 'X'. More formally you need to find the largest square within the grid where all its border cells are 'X'.<br>

Example 1:<br>

Input:
n = 2<br>
a = [[X,X],<br>
     [X,X]]<br>
Output:
2<br>
Explanation:<br>
The largest square submatrix 
surrounded by X is the whole 
input matrix.<br>
Example 2:<br>

Input:
n = 4<br>
a = [[X,X,X,O],<br>
     [X,O,X,X],<br>
     [X,X,X,O],<br>
     [X,O,X,X]]<br>
Output:
3<br>
Explanation:
Here,the input represents following 
matrix of size 4 x 4<br>
X X X O<br>
X O X X<br>
X X X O<br>
X O X X<br>
The square submatrix starting at 
(0,0) and ending at (2,2) is the 
largest submatrix surrounded by X.
Therefore, size of that matrix would be 3.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function largestSubsquare() which takes the integer n and the matrix a as input parameters and returns the size of the largest subsquare surrounded by 'X'.<br>

Expected Time Complexity: O(n^2)<br>
Expected Auxillary Space: O(n^2)<br>

Constraints:<br>
1 <= n <= 1000<br>
a[i][j] belongs to {'X','O'} <br>



__Intuition - > Use two vectors to keep track of no. of X(s) , use prefix sum for the same. Then , use those to calculate X(s) on other two sides.__

```C++
int largestSubsquare(int n, vector<vector<char>> a) {
        // code here
        vector<vector<int>>psR(n,vector<int>(n,0));
        vector<vector<int>>psC(n,vector<int>(n,0));
        
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                psR[i][j]= (a[i][j]=='X'? (j==0 ? 1 : psR[i][j-1] + 1) : 0);
                psC[j][i]= (a[j][i]=='X'? (j==0 ? 1 : psC[j-1][i] + 1) : 0);
            }
        }
        
        int max = 0;
        
        for(int i=n-1;i>=0;i--){
            for(int j=n-1;j>=0;j--){
                int size = min(psR[i][j],psC[i][j]);
                while(size>max){
                    if(psR[i-size+1][j] >=size && psC[i][j-size+1] >=size){
                        max=size;
                        break;
                    }else{
                        size--;
                    }
                }
            }
        }
        return max;
        
        
        
        
        
    }
```
