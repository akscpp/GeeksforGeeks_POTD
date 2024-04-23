[Problem Link](https://www.geeksforgeeks.org/problems/rohans-love-for-matrix4723/1)<br>

Rohan has a special love for the matrices especially for the first element of the matrix. Being good at Mathematics, he also loves to solve the different problem on the matrices. So one day he started to multiply the matrix with the original matrix.  The elements of the original matrix a are given by [a00=1 , a01=1, a10=1, a11=0].
Given the power of the matrix, n calculate the an and return the a10 element mod 1000000007.<br>

Example 1:<br>

Input: 
n = 3<br>
Output: 
2 <br>
Explanation: Take the cube of the original matrix 
i.e a3 and the (a10)th element is 2.<br>
Example 2:<br>

Input: 
n = 4<br>
Output: 
3<br>
Explanation: Take the cube of the original matrix 
i.e a4 and the (a10)th element is 3.<br>
Your Task:  
You dont need to read input or print anything. Complete the function firstElement() which takes n as input parameter and returns the a10 element mod 1000000007 of an.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1<= n <=10^6<br>

__Intuition ->After findind A^2 , A^3 , A^4 ... , it will become clear that the A10 element is a part if Fibonacci series. Just use Fibonacci series Space optimised code.__

```C++
long long int MOD = 1e9+7;
    int firstElement(int n) {
        // code here
        int prev0 = 1 , prev1 = 1;
        
        for(int i = 2 ; i < n ; i++){
            
            int curr = (prev0 + prev1)%MOD;
            
            prev0 = prev1 % MOD;
            
            prev1 = curr % MOD;
        }
        
        return prev1;
    }
```
