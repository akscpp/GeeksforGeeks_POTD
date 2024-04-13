[Problem Link](https://www.geeksforgeeks.org/problems/reverse-bits3556/1)<br>
Given a number x, reverse its binary form and return the answer in decimal.<br>

Example 1:<br>

Input:
x = 1<br>
Output:
2147483648 <br>
Explanation:
Binary of 1 in 32 bits representation-
00000000000000000000000000000001<br>
Reversing the binary form we get, 
10000000000000000000000000000000,<br>
whose decimal value is 2147483648.<br>
Example 2:<br>

Input:
x = 5<br>
Output:
2684354560 <br>
Explanation:
Binary of 5 in 32 bits representation-
00000000000000000000000000000101<br>
Reversing the binary form we get, 
10100000000000000000000000000000,<br>
whose decimal value is 2684354560.<br>
Your Task:
You don't need to read input or print anything. Your task is to complete the function reversedBits() which takes an Integer x as input and returns the reverse binary form of x in decimal form.<br>

Expected Time Complexity: O(log (x))<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
0  <=  x  <  2^32<br>

__Intuition -> Start multiplying 2^31 from MSB ,then 2^30 , then 2^30... as we move from LSB to MSB.__

```C++
long long reversedBits(long long x) {
        // code here
        long long res=0;
        long long i=31;
        
        while(x){
            res+=(long long)(pow(2,i)*(x&1));
            i--;
            x=x>>1;
        }
        return res;
    }
```
