[Problem Link](https://www.geeksforgeeks.org/problems/remove-duplicates3034/1)<br>
Given a string str without spaces, the task is to remove all duplicate characters from it, keeping only the first occurrence.<br>

Note: The original order of characters must be kept the same. <br>

Examples :<br>

Input: str = "zvvo"<br>
Output: "zvo"<br>
Explanation: Only keep the first occurrence<br>
Input: str = "gfg"<br>
Output: "gf"<br>
Explanation: Only keep the first occurrence<br>
Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>
<br>
Constraints:<br>
1 <= |str| <= 10^5<br>
str contains lowercase English alphabets<br>

__Intuition ->Use a freq array of size 26 to store freq of characters one by one. Include only those characters whose frequency is 0 , then increase their frequency.__

```C++
string removeDups(string str) {
        vector<int>freq(26,0);
        
        int n = str.length();
        string ans="";
        
        for(int i=0;i<n;i++){
            if(freq[str[i]-'a']==0){
                ans+=str[i];
                freq[str[i]-'a']++;
            }
        }
        return ans;
    }
```

