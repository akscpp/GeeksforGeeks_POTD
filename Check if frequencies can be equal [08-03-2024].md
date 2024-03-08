Given a string s which contains only lower alphabetic characters, check if it is possible to remove at most one character from this string in such a way that frequency of each distinct character
becomes same in the string. Return true if it is possible to do else return false.

Note: The driver code print 1 if the value returned is true, otherwise 0.
Example 1:
Input:
s = "xyyz"
Output: 
1 
Explanation: 
Removing one 'y' will make frequency of each character to be 1.

Example 2:
Input:
s = "xxxxyyzz"
Output: 
0
Explanation: 
Frequency can not be made same by removing at most one character.
Your Task:  
You dont need to read input or print anything. Complete the function sameFreq() which takes a string as input parameter and returns a boolean value denoting if same frequency is possible or not.

Expected Time Complexity: O(|s|) 
Expected Auxiliary Space: O(1)

Constraints:
1 <= |s| <= 10^5


__Intuition - Use hash map to store frequencies. Them use check funtion to check if all frequencies are equal . If yes , return true. Else , iterate over hash array , decrease freq of each character one by one
and check if frequencies become same. If not , increase the freq of current char and go to next character__

```C++
bool check(int freq[]){
        int n = -1;
        
        for(int f=0;f<26;f++){
            if(freq[f]>0){
                if(n==-1){
                    n=freq[f];
                }else if(freq[f]!=n) return false;
                
            }
        }
        return true;
    }
	bool sameFreq(string s) {
    int freq[26] = {0};
    int n = s.length();

    for (int i = 0; i < n; i++) {
        freq[s[i] - 'a']++;
    }

    if (check(freq)) {
        return true;
    }

    for (int i = 0; i < 26; i++) {
        if (freq[i] > 0) {
            freq[i]--;
            if (check(freq)) {
                return true;
            }
            freq[i]++;
        }
    }
    return false;
}
```
