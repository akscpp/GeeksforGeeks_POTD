[Problem Link](https://www.geeksforgeeks.org/problems/optimal-strategy-for-a-game-1587115620/1)<br>
You are given an array arr of size n. The elements of the array represent n coin of values v1, v2, ....vn. You play against an opponent in an alternating way. In each turn, a player selects either the first or last coin from the row, removes it from the row permanently, and receives the value of the coin.<br>
You need to determine the maximum possible amount of money you can win if you go first.<br>
Note: Both the players are playing optimally.<br>

Example 1:<br>

Input:
n = 4<br>
arr[] = {5, 3, 7, 10}<br>
Output: 
15<br>
Explanation: The user collects maximum
value as 15(10 + 5). It is guarantee that we cannot get more than 15 by any possible moves.<br>
Example 2:<br>

Input:
n = 4<br>
arr[] = {8, 15, 3, 7}<br>
Output: 
22<br>
Explanation: The user collects maximum
value as 22(7 + 15). It is guarantee that we cannot get more than 22 by any possible moves.<br>
Your Task:
Complete the function maximumAmount() which takes an array arr[] (represent values of n coins) and n as a number of coins as a parameter and returns the maximum possible amount of money you can win if you go first.<br>

Expected Time Complexity : O(n*n)<br>
Expected Auxiliary Space: O(n*n)<br>

Constraints:<br>
2 <= n <= 10^3<br>
1 <= arr[i] <= 10^6<br>

__Intuition->Here , we have options of picking either first coin or last coin. So , we will go with recursion. For alternate turns , we will use a bool variable and keep turning its value b/w 1 and 0. When it's out turn ,we will add it to our answer.__

```C++
int dp[1001][1001];
    long long fun(int st , int end , int arr[],int play){
        if(st>end){
            
            return 0;
        }
        if(dp[st][end]!=-1){
            return dp[st][end];
        }
        
        long long sum=0;
        if(play==1){
            sum = max(arr[st]+fun(st+1,end,arr,0) , arr[end]+fun(st,end-1,arr,0));
        }else{
            sum = min(0+fun(st+1,end,arr,1) ,0+fun(st,end-1,arr,1) );
        }
        return dp[st][end]=sum;
    }
    long long maximumAmount(int n, int arr[]){
        // Your code here
        memset(dp,-1,sizeof(dp));
        return fun(0,n-1,arr,1);
    }
```
