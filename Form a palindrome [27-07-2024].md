[Problem Link](https://www.geeksforgeeks.org/problems/form-a-palindrome1455/1)<br>

Given a string, find the minimum number of characters to be inserted to convert it to a palindrome.<br>

Examples :<br>

Input: str = "abcd"<br>
Output: 3<br>
Explanation: Inserted character marked with bold characters in dcbabcd, here we need minimum three characters to make it palindrome.<br>
Input: str = "aa"<br>
Output: 0<br>
Explanation: "aa" is already a palindrome.<br>
Expected Time Complexity: O(n^2)<br>
Expected Auxiliary Space: O(n^2)<br>

Constraints:<br>
1 ≤ |str| ≤ 500<br>
str contains only lowercase alphabets.<br>

__Intuition ->Use LCS to find longest Palindromic Subsequence . Then , str.length() - LPS will give the minimum length that must be inserted to make the given string a PAlindrome.__

```C++
int longestPS(string &s1 , string &s2,int i, int j,vector<vector<int>>&dp){
        if(i==0 || j==0) return 0;
        if(dp[i][j]!=-1) return dp[i][j];
        
        if(s1[i-1]==s2[j-1]){
            return dp[i][j]=1+longestPS(s1,s2,i-1,j-1,dp);
        }else{
            return dp[i][j]=max(longestPS(s1,s2,i-1,j,dp),longestPS(s1,s2,i,j-1,dp));
        }
    }
    int countMin(string str){
        string x = str;
        reverse(str.begin(),str.end());
        int n = str.length();
        vector<vector<int>>dp(n+1,vector<int>(n+1,-1));
        int lps = longestPS(x,str,n,n,dp);
        return n-lps;
    }
```
