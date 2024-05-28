[Problem Link](https://www.geeksforgeeks.org/problems/minimum-cost-to-fill-given-weight-in-a-bag1956/1)<br>

Given an array cost[] of positive integers of size n and an integer w, where cost[i] represents the cost of an i kg packet of oranges, the task is to find the minimum cost to buy exactly w kg of oranges. The cost array has a 1-based indexing. If buying exactly w kg of oranges is impossible, then return -1.<br>
Note:<br>
1. cost[i] = -1 means that i kg packet of orange is unavailable.<br>
2. It may be assumed that there is an infinite supply of all available packet types.<br>

Example 1:<br>

Input: 
n = 5<br>
cost[] = {20, 10, 4, 50, 100} <br>
w = 5<br>
Output: 
14<br>
Explanation: 
Purchase the 2kg packet for 10 coins and the 3kg packet for 4 coins to buy 5kg of oranges for 14 coins.<br>
Example 2:<br>

Input: <br>
n = 5<br>
cost[] = {-1, -1, 4, 3, -1}<br>
w = 5<br>
Output: 
-1<br>
Explanation: 
It is not possible to buy 5 kgs of oranges.<br>
Your Task:  
You don't need to read input or print anything. Complete the function minimumCost() which takes integers n and w, and integer array cost[] as input parameters and returns the minimum cost to buy exactly w kg of oranges, If buying exactly w kg of oranges is impossible, then return -1.<br>

Expected Time Complexity: O(n*w)<br>
Expected Auxiliary Space: O(n*w)<br>

Constraints:<br>
1 ≤ n, w ≤ 2*10^2<br>
1 ≤ cost[i] ≤ 10^5<br>
cost[i] ≠ 0<br>

__Intuition ->Use DP (concept of pick and not-pick).Since there is infinite supply , don't move to next index after picking up the item from the current index.__

```C++
int fun(int ind , int w , vector<int>& cost , int n,vector<vector<int>>&dp){
        
        if(w==0){
            return 0;
        }
        
        if(w<0 || ind>=n){
            return 1e9;
        }
        
        if(dp[ind][w]!=-1) return dp[ind][w];
        
        
        
        int take=1e9;
        int nT=1e9;
        
        if(w - (ind+1) >= 0 && cost[ind]!=-1){
            take = cost[ind] + fun(ind,w-(ind+1),cost,n,dp);
        }
        
        nT = 0 + fun(ind+1,w,cost,n,dp);
        
        return dp[ind][w]=min(take,nT);
    }
    int minimumCost(int n, int w, vector<int> &cost) {
        // code here
        
        vector<vector<int>>dp(n,vector<int>(w+1,-1));
        int ans=fun(0,w,cost,n,dp);
        
        return (ans==1e9)?-1:ans;
    }
```
