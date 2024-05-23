[Problem Link](https://www.geeksforgeeks.org/problems/find-if-string-is-k-palindrome-or-not1923/1)<br>
Given a string str of length n, find if the string is K-Palindrome or not. A k-palindrome string transforms into a palindrome on removing at most k characters from it.<br>


Example 1:<br>

Input: str = "abcdecba"<br>
n = 8, k = 1<br>
Output: 1<br>
Explaination: By removing 'd' or 'e'
we can make it a palindrome.<br>

Example 2:<br>

Input: str = "abcdefcba"<br>
n = 9, k = 1<br>
Output: 0<br>
Explaination: By removing a single 
character we cannot make it a palindrome.<br>

Your Task:<br>
You do not need to read input or print anything. Your task is to complete the function kPalindrome() which takes string str, n, and k as input parameters and returns 1 if str is a K-palindrome else returns 0.<br>


Expected Time Complexity: O(n*n)<br>
Expected Auxiliary Space: O(n*n)<br>


Constraints:<br>
1 ≤ n, k ≤ 10^3<br>

__Intuition->Use LCS to find the length of longest common subsequence. Subtract it from length of string to get the no. of minimim deletions required to make the string palindrome. If this no. is less than k , then return 1 else return 0.__

```C++
// int lcs(string s1,string s2,int ind1,int ind2,vector<vector<int>>&dp){
    //     if(ind1<0|| ind2<0)return 0;
        
    //     if(dp[ind1][ind2]!=-1){
    //         return dp[ind1][ind2];
    //     }
        
    //     if(s1[ind1]==s2[ind2]){
    //         return dp[ind1][ind2] = 1+ lcs(s1,s2,ind1-1,ind2-1,dp);
    //     }
        
    //     return dp[ind1][ind2] = 0 + max(lcs(s1,s2,ind1-1,ind2,dp),lcs(s1,s2,ind1,ind2-1,dp));
    // }

    int kPalindrome(string s1, int n, int k)
    {
        // code here
        string s2=s1;
        reverse(s1.begin(),s1.end());
        int t[n+1][n+1];
        
        for(int i=0;i<=n;i++){
            for(int j=0;j<=n;j++){
                if(i==0||j==0){
                    t[i][j]=0;
                }
            }
        }
        
        for(int i=1;i<=n;i++){
            for(int j=1;j<=n;j++){
                if(s1[i-1]==s2[j-1]){
                    t[i][j]=1+t[i-1][j-1];
                }
                else{
                    t[i][j]=max(t[i-1][j],t[i][j-1]);
                }
            }
        }
        int min_deletions= n-t[n][n];
        return min_deletions<=k;
    }
```
