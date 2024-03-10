Given a string str which may contains lowercase and uppercase chracters. The task is to remove all duplicate characters from the string and find the resultant string. The order of remaining characters in the output should be same as in the original string.<br>

Example 1:<br>

Input:<br>
str = "geEksforGEeks"<br>
Output:
"geEksforG"<br>
Explanation: 
After removing duplicate characters such as E, e, k, s, we have string as "geEksforG".<br>
Example 2:<br>

Input:<br>
str = "HaPpyNewYear"<br>
Output: 
"HaPpyNewYr"<br>
Explanation:
After removing duplicate characters such as e, a, we have string as "HaPpyNewYr".<br>
Your Task:<br>
Complete the function removeDuplicates() which takes a string str, as input parameters and returns a string denoting the answer. You don't have to print answer or take inputs.<br>

Expected Time Complexity: O(N)<br>
Expected Auxiliary Space: O(N)<br>

Constraints:<br>
1 ≤ N ≤ 10^5<br>
String contains uppercase and lowercase english letters.<br>


_Intuition -> Use a map to keep track of letters. Initially , initialise the keys of letter in map as -1 . Then , while traversing string , if string key has -1 , include it in answer and update the value of the corresponding string key as 0.We will only add the string in the answer if the value of the key is -1 , else we ignore the element.__

```C++
string removeDuplicates(string str) {
	    // code here
	    unordered_map<char,int>mp;
	    int n = str.length();
	    for(int i=0;i<n;i++){
	        mp[str[i]]=-1;
	    }
	    
	    string ans = "";
	    
	    for(int i=0;i<n;i++){
	        if(mp[str[i]]==-1){
	            ans+=str[i];
	            mp[str[i]]=0;
	        }
	    }
	    return ans;
	}
```
