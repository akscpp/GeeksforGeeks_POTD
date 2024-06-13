[Problem Link](https://www.geeksforgeeks.org/problems/padovan-sequence2855/1)<br>

Given a number n, find the nth number in the Padovan Sequence.<br>

A Padovan Sequence is a sequence which is represented by the following recurrence relation<br>
P(n) = P(n-2) + P(n-3)<br>
P(0) = P(1) = P(2) = 1<br>

Note: Since the output may be too large, compute the answer modulo 10^9+7.<br>

Examples :<br>

Input: n = 3<br>
Output: 2<br>
Explanation: We already know, P1 + P0 = P3 and P1 = 1 and P0 = 1<br>
Input: n = 4<br>
Output: 2<br>
Explanation: We already know, P4  = P2 + P1 and P2 = 1 and P1 = 1<br>
Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 <= n <= 10^6<br>

__Intuition ->Use 3 variables to store the last 3 values and keep updating them until n is reached.__

```C++
int MOD = 1e9+7;
    int padovanSequence(int n)
    {
        if(n<=2) return 1;
        
        int n_1 = 1;
        int n_2 = 1;
        int n_3 = 1;

        
        for(int i=3;i<=n;i++){
            
            int curr = (n_2 + n_3)%MOD;
            
            n_3 = n_2;
            n_2 = n_1;
            n_1 = curr;
        }
        
        return n_1;
    }
```
