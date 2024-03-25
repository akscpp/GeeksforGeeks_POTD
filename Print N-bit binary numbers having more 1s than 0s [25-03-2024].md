[Problem Link](https://www.geeksforgeeks.org/problems/print-n-bit-binary-numbers-having-more-1s-than-0s0252/1)<br>

Given a positive integer n. Your task is to generate a string list of all n-bit binary numbers where, for any prefix of the number, there are more or an equal number of 1's than 0's. The numbers should be sorted in decreasing order of magnitude.<br>

Example 1:<br>

Input:  
n = 2<br>
Output: 
"11, 10"<br>
Explanation: Valid numbers are those where each prefix has more 1s than 0s:<br>
11: all its prefixes (1 and 11) have more 1s than 0s.<br>
10: all its prefixes (1 and 10) have more 1s than 0s.<br>
So, the output is "11, 10".<br>
Example 2:<br>

Input:  
n = 3<br>
Output: 
"111, 110, 101"<br>
Explanation: Valid numbers are those where each prefix has more 1s than 0s.<br>
111: all its prefixes (1, 11, and 111) have more 1s than 0s.<br>
110: all its prefixes (1, 11, and 110) have more 1s than 0s.<br>
101: all its prefixes (1, 10, and 101) have more 1s than 0s.<br>
So, the output is "111, 110, 101".<br>
User Task:<br>
Your task is to complete the function NBitBinary() which takes a single number as input n and returns the list of strings in decreasing order. You need not take any input or print anything.<br>

Expected Time Complexity: O(|2^n|)<br>
Expected Auxiliary Space: O(2^n)<br>

Constraints:
1 <= n <= 15<br>

__Intuition -> Use recursion. Start with curr = " " and do curr+"1" and curr+"0" . Also , keep count of 1s and 0s. If count1 < count0, don't add the string to ans. If c1>=c0 , ad the resultant string to ans.__

```C++
void fun(int n,string curr,int c1,int c0,vector<string>& ans){
        if(c1<c0) return;
        
        if(curr.length()==n){
            ans.push_back(curr);
            return;
        }
        
        fun(n,curr+"1",c1+1,c0,ans);
        fun(n,curr+"0",c1,c0+1,ans);
        return;
    }
	vector<string> NBitBinary(int n)
	{
	    // Your code goes here
	    int c1=0,c0=0;
	    vector<string>ans;
	    fun(n,"",c1,c0,ans);
	    return ans;
	}
```
