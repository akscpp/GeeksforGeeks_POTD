[Problem Link](https://www.geeksforgeeks.org/problems/geek-and-its-game-of-coins4043/1)<br>
Given three numbers n, x, and y, Geek and his friend are playing a coin game. In the beginning, there are n coins. In each move, a player can pick x, y, or 1 coin. Geek always starts the game. The player who picks the last coin wins the game. The task is to determine whether Geek will win the game or not if both players play optimally.<br>

Example 1:<br>

Input:<br>
n = 5<br>
x = 3<br>
y = 4<br>
Output: 
1<br>
Explanation:
There are 5 coins, every player can pick 1 or 3 or 4 coins on his/her turn. Geek can win by picking 3 coins in first chance. Now 2 coins will be left so his friend will pick one coin and now Geek can win by picking the last coin.<br>
Example 2:<br>
Input:<br>
n = 2<br>
x = 3<br>
y = 4<br>
Output:
0<br>
Explanation: 
Geek picks 1 coin and then his friend picks 1 coin.<br>
Your Task: 
You don't need to read input or print anything. Complete the function findWinner() which takes n, x, and y as input parameters and returns 1 if Geek can win otherwise 0.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>
 
Constraints:<br>
1 ≤ n, x, y ≤ 10^5<br>

__Intuition ->Use DP. If n is 0 , then geek loses. If n is 1 , geek wins. Alternatively fill the dp array based on the given condition of n , x , y.__

```C++
int findWinner(int n, int x, int y) {
        // code here
        vector<int>dp(n+1,0);
        dp[0]=0;
        dp[1]=1;
        
        for(int i=2;i<=n;i++){
            if(i-1>=0 and dp[i-1]==0){
                dp[i]=1;
            }
            
            else if(i-x>=0 and dp[i-x]==0){
                dp[i]=1;
            }
            
            else if(i-y>=0 and dp[i-y]==0){
                dp[i]=1;
            }
            
            else{
                dp[i]=0;
            }
        }
        
        return dp[n];
    }
```
