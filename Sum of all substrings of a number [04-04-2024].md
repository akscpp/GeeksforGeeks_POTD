[Problem Link](https://www.geeksforgeeks.org/problems/sum-of-all-substrings-of-a-number-1587115621/1)<br>
Given an integer s represented as a string, the task is to get the sum of all possible sub-strings of this string.<br>
As the answer will be large, return answer modulo 109+7. <br>

Note: The number may have leading zeros.<br>

Example 1:<br>

Input:
s = "1234"<br>
Output: 
1670<br>
Explanation: 
Sum = 1 + 2 + 3 + 4 + 12 + 23 + 34 + 123 + 234 + 1234 = 1670<br>
Example 2:<br>

Input:
s = "421"<br>
Output: 
491<br>
Explanation: 
Sum = 4 + 2 + 1 + 42 + 21 + 421 = 491<br>
Your Task:
You only need to complete the function sumSubstrings that takes s as an argument and returns the answer modulo 109+7.<br>

Expected Time Complexity: O(|s|).<br>
Expected Auxiliary Space: O(|s|).<br>

Constraints:
1 <= |s| <= 10^5<br>

__Intuition -> Calculate sum till the current index and keep adding it to the final answer.__ <br>

__s= "1234"__ <br>
__sum [all substribgs ending at 4th index (0 - based indexing)] = 1234 + 234 + 34 + 4__ <br>
__= 4 + (30+4) + (230+4) + (1230+4)__ <br>
__= 4 (4) + (3 + 23 + 1234)*10__ <br>
__= 4 (3 + 1) + sum[till 3rd index] * 10__ <br>
__= (s[i] - '0') * (i+1) + sum[all substribgs ending at 3rd index (0 - based indexing)] * 10__ <br>

```C++
long long sumSubstrings(string s){
        
        // your code here
        int n = s.length();
        long long prev = 0;
        long long ans=0;
        long long curr=0;
        long long MOD = 1e9+7;
        
        for(int i=0;i<n;i++){
            curr = (s[i]-'0')*(i+1)+prev*10;
            curr%=MOD;
            ans+=curr;
            ans%=MOD;
            prev=curr;
        }
        return ans;
    }
```

