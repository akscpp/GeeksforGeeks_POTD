[Problem Link](https://www.geeksforgeeks.org/problems/find-number-of-times-a-string-occurs-as-a-subsequence3020/1)<br>
Given two strings, s1 and s2, count the number of subsequences of string s1 equal to string s2.<br>

Return the total count modulo 1e9+7.<br>

Example 1:<br>

Input: s1 = geeksforgeeks, s2 = gks<br>
Output: 4<br>
Explaination: We can pick characters from s1 as a subsequence from indices {0,3,4}, {0,3,12}, {0,11,12} and {8,11,12}.So total 4 subsequences of s1 that are equal to s2.<br>
Example 2:<br>

Input: s1 = problemoftheday, s2 = geek<br>
Output: 0<br>
Explaination: No subsequence of string s1 is equal to string s2.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function countWays() which takes the string s1 and s2 as input parameters and returns the number of subsequences of s1 equal to s2.<br>

Expected Time Complexity: O(n*m)  [n and m are lengths of the strings s1 and s2]<br>
Expected Auxiliary Space: O(n*m)     [n and m are lengths of the strings s1 and s2]<br>

Constraints:<br>
1 ≤ n, m ≤ 500  [n and m are lengths of the strings s1 and s2]<br>

__Intuition ->Use concept of pick and not pick of recursion. If current length of string temp is less than s2 and temp[i] is equal to s2[curr_length] , then increase the current length by 1 and move to next index.Else move to next index without increasing the current length.__

```C++
int MOD = 1e9+7;
    int fun(int idx , int curr_len , string& s1 , string& s2,vector<vector<int>>& dp){
        
        if(curr_len == s2.length()){
            return 1;
        }
        if (idx >= s1.length()) return 0;
        
        if(dp[idx][curr_len]!=-1) return dp[idx][curr_len];
        
        int pick = 0,nPick = 0;
        
        if(curr_len<s2.length() && s1[idx]==s2[curr_len]){
            pick = fun(idx+1,curr_len+1,s1,s2,dp);
        }
        
        nPick = fun(idx+1,curr_len,s1,s2,dp);
        
        return dp[idx][curr_len]=(pick+nPick)%MOD;
    }
    int countWays(string s1, string s2) {
        // code here
        vector<vector<int>>dp(s1.length()+1,vector<int>(s2.length()+1,-1));
        return fun(0,0,s1,s2,dp);
    }
```
