[Problem Link](https://www.geeksforgeeks.org/problems/paths-to-reach-origin3850/1)<br>
You are standing on a point (x, y) and you want to go to origin (0, 0) by taking steps either left or up i.e. from each point you are allowed to move either in (x-1, y) or (x, y-1). Find the number of paths from point to origin.<br>

Example 1:<br>

Input:
x = 3, y = 0 <br>
Output: 
1<br>
Explanation: Path used was -  (3,0)  --> ( 2,0) --> (1,0) --> (0,0).We can see that there is no other path than this, so we return 1.<br>
Example 2:<br>

Input:
x = 3, y = 6<br>
Output: 
84 <br>
Explanation:
There are total 84 possible paths.<br>
Your Task:
Since, this is a function problem. You don't need to take any input, as it is already accomplished by the driver code. You just need to complete the function ways() that takes integer x and  y as parameters and returns the total number of paths from point(x,y) to the origin(0,0) % 1000000007.<br>

Expected Time Complexity: O(x*y).<br>
Expected Auxiliary Space: O(x*y).<br>

Constraints:<br>
1 ≤ x, y ≤ 500<br>

__Intuition -> USE DP. Go from (x,y) to (0,0) using the given way , i.e, (x-1,y) or (x,y-1).__

```C++
int MOD = 1000000007;

    // MEMOIZATION
    // int fun(int x , int y, vector<vector<int>> &dp){
    //     if(x==0 && y==0) return 1;
        
    //     if(x<0 || y<0) return 0;
        
    //     if(dp[x][y]!=-1) return dp[x][y];
        
    //     int left = fun(x-1,y,dp)%MOD;
    //     int up = fun(x,y-1,dp)%MOD;
        
    //     return dp[x][y]=(up+left)%MOD;
    // }

    int ways(int x, int y)
    {
        //code here.
        //vector<vector<int>>dp(x+1,vector<int>(y+1,0));
        // return fun(x,y,dp);
        
        //TABULATION
        // dp[0][0]=1;
        
        // for(int i=0;i<=x;i++){
        //     for(int j=0;j<=y;j++){
        //         if(i==0 && j==0) dp[i][j]=1;
        //         else{
        //             int left = 0;
        //             if(i-1>=0) left = dp[i-1][j]%MOD;
        //             int up =0;
        //             if(j-1>=0) up = dp[i][j-1]%MOD;
                    
        //             dp[i][j]=up%MOD+left%MOD;
        //         }
        //     }
        // }
        // return dp[x][y]%MOD;
        
        
        //SPACE OPTIMISED
        vector<int>prev(y+1,0);
        
        for(int i=0;i<=x;i++){
            vector<int>curr(y+1,0);
            for(int j=0;j<=y;j++){
                if(i==0 && j==0) curr[j]=1;
                else{
                    int left = 0;
                    if(i-1>=0) left = prev[j]%MOD;
                    int up =0;
                    if(j-1>=0) up = curr[j-1]%MOD;
                    
                    curr[j]=(up+left)%MOD;
                }
                
            }
            prev = curr;
        }
        
        return prev[y];
    }
```
