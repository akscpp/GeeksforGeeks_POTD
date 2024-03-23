[Problem Link](https://www.geeksforgeeks.org/problems/fibonacci-series-up-to-nth-term/1)<br>
You are given an integer n, return the fibonacci series till the nth(0-based indexing) term. Since the terms can become very large return the terms modulo 10^9+7.<br>

Example 1:<br>

Input:
n = 5<br>
Output:
0 1 1 2 3 5<br>
Explanation:
0 1 1 2 3 5 is the Fibonacci series up to the 5th term.<br>
Example 2:<br>

Input:
n = 10<br>
Output:
0 1 1 2 3 5 8 13 21 34 55<br>
Explanation:
0 1 1 2 3 5 8 13 21 34 55 is the Fibonacci series up to the 10th term.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function Series() which takes an Integer n as input and returns a Fibonacci series up to the nth term.<br>

Expected Time Complexity: O(n)<br>
Expected Space Complexity: O(n)<br>

Constraint:<br>
1 <= n <= 10^5<br>

__Intuition -> Use a vector to store values and using last 2 values , calculate the current value. Also , use MOD 1e9+7.__

```C++
vector<int> Series(int n) {
        // Code here
        vector<int>dp(n+1,0);
        const int MOD = 1e9+7;
        dp[0]=0;
        if(n==0) return dp;
        dp[1]=1;
        if(n==1) return dp;
        
        for(int i=2;i<=n;i++){
            dp[i]=(dp[i-1]+ dp[i-2])%MOD;
        }
        return dp;
    }
```
