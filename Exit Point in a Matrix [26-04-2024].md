[Problem Link](https://www.geeksforgeeks.org/problems/exit-point-in-a-matrix0905/1)<br>

Given a matrix of size n x m with 0’s and 1’s, you enter the matrix at cell (0,0) in left to right direction. Whenever you encounter a 0 you retain it in the same direction, else if you encounter a 1 you have to change the direction to the right of the current direction and change that 1 value to 0, you have to find out from which index you will leave the matrix at the end.<br>

Example 1:<br>

Input: 
n = 3, m = 3<br>
matrix = {{0, 1, 0},<br>
          {0, 1, 1}, <br>
          {0, 0, 0}}<br>
Output: 
{1, 0}<br>
Explanation: <br>
Enter the matrix at (0, 0) <br>
-> then move towards (0, 1) ->  1 is encountered <br>
-> turn right towards (1, 1)  -> again 1 is encountered <br>
-> turn right again towards (1, 0) <br>
-> now, the boundary of matrix will be crossed ->hence, exit point reached at 1, 0..<br>
Example 2:<br>

Input: <br>
n = 1, m = 2<br>
matrix = {{0, 0}}<br>
Output: 
{0, 1}<br>
Explanation:<br> 
Enter the matrix at cell (0, 0).<br>
Since the cell contains a 0, we continue moving in the same direction.<br>
We reach cell (0, 1), which also contains a 0. So, we continue moving in the same direction, we exit the matrix from cell (0, 1).<br>
Your Task:<br>
You don't need to read or print anything. Your task is to complete the function FindExitPoint() which takes the matrix as an input parameter and returns a list containing the exit point.<br>

Expected Time Complexity: O(n * m) where n = number of rows and m = number of columns.<br>
Expected Space Complexity: O(1)<br>

Constraints:<br>
1 <= n, m <= 100<br>

__Intuition->Use a single veriable to keep track of direction of movement. When 1 is encountered , store the current row and column and move to the respected cell. Also , before moving to next cell , don't forget to change the 1 (if encountered) to 0.__

```C++
vector<int> FindExitPoint(int n, int m, vector<vector<int>>& mat) {
        // Code here
        int dir=0;
        //0 -> left to right
        //1 -> up to down
        //2 -> right to left
        //3 -> down to up
        
        int i=0,j=0;
        int c=0,r=0;
        
        while(i>=0 && j>=0 && i<n && j<m){
            if(dir==0){
                if(mat[i][j]==0) {
                    r=i;
                    c=j;
                    j++;
                }else{
                    dir=1;
                    r=i;
                    c=j;
                    mat[i][j]=0;
                    i++;
                }
            }else if(dir==1){
                if(mat[i][j]==0){
                    r=i;
                    c=j;
                    i++;
                }else{
                    dir=2;
                    c=j;
                    r=i;
                    mat[i][j]=0;
                    j--;
                }
            }else if(dir==2){
                if(mat[i][j]==0){
                    c=j;
                    r=i;
                    j--;
                }else{
                    dir=3;
                    r=i;
                    c=j;
                    mat[i][j]=0;
                    i--;
                }
            }else if(dir==3){
                if(mat[i][j]==0){
                    r=i;
                    c=j;
                    i--;
                }else{
                    dir=0;
                    c=j;
                    r=i;
                    mat[i][j]=0;
                    j++;
                }
            }
            
            
            if(i<0 || j<0 || j>=m || i>=n){
                break;
            }
        }
        return {r,c};
    }
```
