[Problem Link](https://www.geeksforgeeks.org/problems/help-nobita0532/1)<br>
Given a string s of lowercase English characters, determine whether the summation of x and y is EVEN or ODD.
where:<br>

x is the count of distinct characters that occupy even positions in the English alphabet and have even frequency. <br>
y is the count of distinct characters that occupy odd positions in the English alphabet and have odd frequency.<br>
Ex: string = "ab" here 'a' has an odd(1) position in the English alphabet & has an odd(1) frequency in the string so a is odd but b has an even(2) position in the English alphabet & has odd(1) frequency so it doesn't count(since string doesn't have 2 b's) so the final answer x + y = 1+0 = 1(odd) would be "ODD".<br>

Note: Return "EVEN" if the sum of x & y is even otherwise return "ODD".<br>

Example 1:<br>

Input: 
s = "abbbcc"<br>
Output: 
ODD<br>
Explanation: 
x = 0 and y = 1 so (x + y) is ODD. 'a' occupies 1st place(odd) in english alphabets and its frequency is odd(1), 'b' occupies 2nd place(even) but its frequency is odd(3) so it doesn't get counted and 'c' occupies 3rd place(odd) but its frequency is even(2) so it also doesn't get counted.<br>
Example 2:<br>

Input: 
s = "nobitaa"<br>
Output: 
EVEN<br>
Explanation: 
Here n, b, t & a would not count since doesn't match with the even condition but o & i will be counted as it satisfies the odd conditions so x = 0 and y = 2 so (x + y) is EVEN.<br>
Your Task:  
You don't need to read input or print anything. Complete the function evenOdd() which takes s as input parameter and returns "EVEN"  if x + y is even, and returns "ODD" otherwise.<br>

Expected Time Complexity: O(|s|)<br>
Expected Auxiliary Space: O(1) <br>

Constraints:
1 ≤ |s| ≤ 10^5

__Intuition ->Store the frequency of each character in an array of size 26. Now , iterate over string and check the condition . Also , when a character has been taken into account , set its frequency to 0 to avoid counting it again (if it appears later in the string again).__

```C++
string oddEven(string s) {
        // code here
        vector<int>ch(27,0);
        int n = s.length();
        
        for(int i=0;i<n;i++){
            ch[s[i]-'a']++;
        }
        
        int x = 0, y = 0;
        
        for(int i=0;i<n;i++){
            int freq = ch[s[i]-'a'];
            
            if(freq>0){
                ch[s[i]-'a']=0;
            
                if((int(s[i])%2==0 && freq%2==0)) x++;
                else if((int(s[i])%2!=0 && freq%2!=0)) y++;
            }
            
        }
        
        return ((x+y)%2==0)?"EVEN":"ODD";
    }
```
