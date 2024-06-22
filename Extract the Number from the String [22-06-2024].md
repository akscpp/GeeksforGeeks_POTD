[Problem Link](https://www.geeksforgeeks.org/problems/extract-the-number-from-the-string3428/1)<br>

Given a sentence containing several words and numbers. Find the largest number among them which does not contain 9. If no such number exists, return -1.<br>

Note: Numbers and words are separated by spaces only.<br>

Examples :<br>

Input: sentence="This is alpha 5057 and 97"<br>
Output: 5057<br>
Explanation: 5057 is the only number that does not have a 9.<br>
Input: sentence="Another input 9007"<br>
Output: -1<br>
Explanation: Since there is no number that does not contain a 9,output is -1.<br>
Expected Time Complexity: O(n)<br>
Expected Auxillary Space: O(n)<br>

Constraints:<br>
1<=n<=10^6<br>
1<=answer<=10^18<br>

n is the length of a given sentence.
__Intuition->Scans through a string to extract the largest number that doesn't contain the digit '9'.Accumulate digits to form numbers, checks for spaces to evaluate completed numbers, and maintain a flag to discard numbers containing '9'. If no valid number is found, return -1.__

```C++
long long ExtractNumber(string sentence) {

        long long ans=0,temp=0;
        
        bool flag = false;
        
        for(char x:sentence){
            if(x>='0' && x<='9'){
                temp = temp*10+(x-'0');
                
                if(x=='9') flag = true;
                
            }else if(x==' '){
                if(!flag){
                    ans = max(ans,temp);
                }
                
                flag = false;
                temp=0;
            }
        }
        
        if(!flag){
            ans = max(ans,temp);
        }
        
        return (ans==0)?-1:ans;
    }
```
