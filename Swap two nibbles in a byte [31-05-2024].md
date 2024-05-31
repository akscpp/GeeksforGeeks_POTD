[Problem Link](https://www.geeksforgeeks.org/problems/swap-two-nibbles-in-a-byte0446/1)<br>
Given a number n, Your task is to swap the two nibbles and find the resulting number. <br>

A nibble is a four-bit aggregation, or half an octet. There are two nibbles in a byte. For example, the decimal number 150 is represented as 10010110 in an 8-bit byte. This byte can be divided into two nibbles: 1001 and 0110.<br>

Example 1:<br>

Input: n = 100<br>
Output: 70<br>
Explanation: 100 in binary is 01100100, two nibbles are (0110) and (0100). If we swap the two nibbles, we get 01000110 which is 70 in decimal.<br>
Example 2:<br>

Input: n = 129<br>
Output: 24<br>
Explanation: 129 in binary is 10000001, two nibbles are (1000) and (0001). If we swap the two nibbles, we get 00011000 which is 24 in decimal.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function swapNibbles() which takes an integer n as input parameter and returns an integer after swapping nibbles in the binary representation of n.<br>

Expected Time Complexity: O(1)<br>
Expected Space Complexity: O(1)<br>

Constraints:<br>
0 ≤ n ≤ 255<br>

__Intuition ->For extracting lower 4 bit and higher 4 bit nibbles , use left and right shift operators.But , before applying right shift on lower nibble , use 0x0F for bit masking and preserving the lower nibble.__

```C++
int swapNibbles(int n) {
        // code here
        return (n&0x0F)<<4 | (n>>4);
    }
```
