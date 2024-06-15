[Problem Link](https://www.geeksforgeeks.org/problems/mobile-numeric-keypad5456/1)<br>

There is a standard numeric keypad on a mobile phone. You can only press the current button or buttons that are directly up, left, right, or down from it (for ex if you press 5, then pressing 2, 4, 6 & 8 are allowed). Diagonal movements and pressing the bottom row corner buttons (* and #) are prohibited.<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/34181111-37e5-4629-825c-2d0f6947b209)<br>


Given a number n, find the number of possible unique sequences of length n that you can create by pressing buttons. You can start from any digit.<br>

Examples<br>

Input: n = 1<br>
Output: 10<br>
Explanation: Number of possible numbers are 10 (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)  <br>
Input: n = 2<br>
Output: 36<br>
Explanation: Possible numbers: 00, 08, 11, 12, 14, 22, 21, 23, 25 and so on. If we start with 0, valid numbers will be 00, 08 (count: 2). If we start with 1, valid numbers will be 11, 12, 14 (count: 3). If we start with 2, valid numbers  will be 22, 21, 23,25 (count: 4). If we start with 3, valid numbers will be 33, 32, 36 (count: 3). If we start with 4, valid numbers will be 44,41,45,47 (count: 4). If we start with 5, valid numbers will be 55,54,52,56,58 (count: 5) and so on.<br>
Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 ≤ n ≤ 25<br>

__Intuition-> The corrected function uses memoization to efficiently count the number of valid sequences of key presses on a keypad, considering specific constraints such as avoiding certain keys and staying within bounds. It recursively explores all possible moves (up, down, left, right) from each key and sums the results, storing intermediate results in a 3D DP table to avoid redundant calculations, ultimately maximizing the count of valid sequences for n key presses.__

```C++
long long help(int i,int j , int n,vector<vector<vector<long long>>>& dp){
        if(i>3 || j>2 || i<0 || j<0) return 0;
        
        if(i==3 && (j==0 || j==2)) return 0;
        
        if(n==1) return 1;
        
        if(dp[i][j][n]!=-1) return dp[i][j][n];
        n--;
        
        return dp[i][j][n+1]= help(i-1,j,n,dp)+help(i,j-1,n,dp)+help(i+1,j,n,dp)+
                                        help(i,j+1,n,dp)+help(i,j,n,dp);
        
        
    }
    long long getCount(int n) {
        // Your code goes here
        long long ans = 0;
        
        vector<vector<vector<long long>>> dp(4,vector<vector<long long>>(3,vector<long long>(n+1,-1)));
        
        for(int i=0;i<4;i++){
            for(int j=0;j<3;j++){
                if(i==3 && (j==0 || j==2)) continue;
                
                ans+= help(i,j,n,dp);
            }
        }
        
        return ans;
    }
```
