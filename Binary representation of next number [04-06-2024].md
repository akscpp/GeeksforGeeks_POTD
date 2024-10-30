[Problem Link](https://www.geeksforgeeks.org/problems/binary-representation-of-next-number3648/1)<br>
Given a binary representation in the form of a string(s) of a number n, the task is to find a binary representation of n+1.<br>

Example 1:<br>

Input: s = "10"<br>
Output: 11<br>
Explanation: "10" is the binary representation of 2 and binary representation of 3 is "11"<br>
Example 2:<br>


Input: s = "111"<br>
Output: 1000<br>
Explanation: "111" is the binary representation of 7 and binary representation of 8 is "1000"<br>
Your Task:  <br>
You don't need to read input or print anything. Complete the function binaryNextNumber()which takes s as input parameter and returns the string.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n) to store resultant string  <br>

Constraints:<br>
1 <= n <= 10^5<br>

__Intuition ->Traverse from right to left.Also , initialise carry as 1 (adding 1). If "1" is encountered and carry is one , make "1" to "0". If "0" is encountered ans carry is 1 , convert "0" to "1".Also, check for leading 0's like 00001 must be converted to 1.__

```C++
string binaryNextNumber(string s) {
        // code here.
       int carry = 1; // Start with adding 1
        int n = s.length();
    
        for (int i = n - 1; i >= 0; i--) {
            if (s[i] == '1') {
                s[i] = '0';
            } else {
                s[i] = '1';
                carry = 0;
                break;
            }   
        }
    
        if (carry == 1) {
            s = '1' + s;
        }
    
        // Remove leading zeros
        size_t start_pos = s.find_first_not_of('0');
        if (start_pos != string::npos) {
            s = s.substr(start_pos);
        } else {
            s = "0"; 
        }

        return s;
    }
```
