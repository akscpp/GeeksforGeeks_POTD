[Problem Link](https://www.geeksforgeeks.org/problems/modular-exponentiation-for-large-numbers5537/1)<br>
Implement pow(x, n) % M.<br>
In other words, for a given value of x, n, and M, find  (x^n) % M.<br>
 

Example 1:<br>

Input:
x = 3, n = 2, m = 4<br>
Output:
1<br>
Explanation:
3^2 = 9. 9 % 4 = 1.<br>
Example 2:<br>

Input:
x = 2, n = 6, m = 10<br>
Output:
4<br>
Explanation:
2^6 = 64. 64 % 10 = 4.<br>

Your Task:
You don't need to read or print anything. Your task is to complete the function PowMod() which takes integers x, n, and M as input parameters and returns x^n % M.<br>
 

Expected Time Complexity: O(log(n))<br>
Expected Space Complexity: O(1)<br>
 

Constraints:
1 ≤ x, n, M ≤ 10^9<br>

__Intuition -> Use recursion to calculate power.__

```C++
long long fun(long long int x, long long int n, long long int M) {
            if (n == 0) return 1;
            if (n == 1) return x % M;
            
            long long temp = fun(x, n / 2, M);
            temp = (temp * temp) % M;
            
            if (n % 2 == 0) return temp;
            return (temp * x) % M;
        }

        long long int PowMod(long long int x, long long int n, long long int M) {
             return fun(x, n, M);
        }
```
