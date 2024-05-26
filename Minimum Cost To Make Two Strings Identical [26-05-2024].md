[Problem Link](https://www.geeksforgeeks.org/problems/minimum-cost-to-make-two-strings-identical1107/1)<br>

Given two strings x and y, and two values costX and costY, the task is to find the minimum cost required to make the given two strings identical. You can delete characters from both the strings. The cost of deleting a character from string X is costX and from Y is costY. The cost of removing all characters from a string is the same.<br>

Example 1:<br>

Input: x = "abcd", y = "acdb", costX = 10
       costY = 20.<br>
Output: 30<br>
Explanation: For Making both strings
identical we have to delete character 
'b' from both the string, hence cost 
will be = 10 + 20 = 30.<br>
Example 2:<br>

Input : x = "ef", y = "gh", costX = 10
        costY = 20.<br>
Output: 60<br>
Explanation: For making both strings 
identical, we have to delete 2-2 
characters from both the strings, hence 
cost will be = 10 + 10 + 20 + 20 = 60.<br>
Your Task:
You don't need to read or print anything. Your task is to complete the function findMinCost() which takes both strings and the costs as input parameters and returns the minimum cost.<br>

Expected Time Complexity: O(|x|*|y|)<br>
Expected Space Complexity: O(|x|*|y|)<br>

Constraints:<br>
1 ≤ |x|, |y| ≤ 1000<br>
1<= costX, costY <= 10^5<br>

__Intuition ->To make two strings indetical , we have to find the common elements between them and delete the ones which are not common. So why not use LCS to find the longest common subsequence between both the strings. Length of string minus the lcs will give the number of elements which are not common.__

```C++
int lcs(int n1 , int n2 , string& x , string& y , vector<vector<int>>&dp){
        
        if(n1<0 || n2<0) return 0;
        
        if(dp[n1][n2]!=-1) return dp[n1][n2];
        
        if(x[n1]==y[n2]){
            return dp[n1][n2] = 1+lcs(n1-1,n2-1,x,y,dp);
        }
        
        return dp[n1][n2]= 0 + max (lcs(n1-1,n2,x,y,dp),lcs(n1,n2-1,x,y,dp));
    }
    int findMinCost(string x, string y, int costX, int costY) {
        // Your code goes here
        
        int n1 = x.length();
        int n2 = y.length();
        
        vector<vector<int>>dp(n1,vector<int>(n2,-1));
        int LCS = lcs(n1-1,n2-1,x,y,dp);
        
        return (n1-LCS)*costX + (n2-LCS)*costY;
    }
```
