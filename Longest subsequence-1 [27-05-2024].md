[Problem Link](https://www.geeksforgeeks.org/problems/longest-subsequence-such-that-difference-between-adjacents-is-one4724/1)<br>
Given an integer array a[] of size n, find the length of the longest subsequence such that the absolute difference between adjacent elements is 1.<br>

Example 1:<br>

Input:
n = 7<br>
a[] = {10, 9, 4, 5, 4, 8, 6}<br>
Output: 
3<br>
Explaination: 
The three possible subsequences of length 3 are {10, 9, 8}, {4, 5, 4}, and {4, 5, 6}, where adjacent elements have a absolute difference of 1. No valid subsequence of greater length could be formed.<br>
Example 2:<br>

Input: 
n = 5<br>
a[] = {1, 2, 3, 4, 5}<br>
Output: 
5<br>
Explaination: 
All the elements can be included in the valid subsequence.<br>
Your Task:
You do not need to read input. Your task is to complete the function longestSubseq() which takes integer n and array a[] as input parameters and returns the length of the longest subsequence where the absolute difference of adjacent elements is 1.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 ≤ n ≤ 10^3<br>
1 ≤ a[i] ≤ 10^3<br>

__Intuition ->Use DP with concept of pick and not-pick. Pick the element if it is first element into consideration or the absolute between is 1.__

```C++
int fun(int idx , int last , vector<int>& a,vector<vector<int>>& dp){
        if (idx == a.size()) {
            return 0;
        }
        
        if(dp[idx][last+1]!=-1) return dp[idx][last+1];
        
        int take = 0 , nT = 0;
        
        if (last == -1 || abs(a[idx] - a[last]) == 1) {
            take = 1 + fun(idx + 1, idx, a,dp);
        }

        nT = 0 + fun(idx + 1, last, a,dp);
        
        return dp[idx][last+1]= max(take,nT);
    }
    int longestSubseq(int n, vector<int> &a) {
        // code here
        
        vector<vector<int>>dp(n,vector<int>(n+1,-1));
        return fun(0,-1,a,dp);
    }
```
