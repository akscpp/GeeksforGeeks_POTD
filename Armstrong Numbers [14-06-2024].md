[Problem Link](https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1)<br>

You are given a 3-digit number n, Find whether it is an Armstrong number or not.<br>


An Armstrong number of three digits is a number such that the sum of the cubes of its digits is equal to the number itself. 371 is an Armstrong number since 3^3 + 7^3 + 1^3 = 371. <br>

Note: Return "true" if it is an Armstrong number else return "false".<br>

Examples<br>


Input: n = 153<br>
Output: true<br>
Explanation: 153 is an Armstrong number since 1^3 + 5^3 + 3^3 = 153. Hence answer is "true".<br>
Input: n = 372<br>
Output: false<br>
Explanation: 372 is not an Armstrong number since 3^3 + 7^3 + 2^3 = 378. Hence answer is "false".<br>

Expected Time Complexity: O(1)<br>
Expected Auxiliary Space: O(1) <br>

Constraints:<br>
100 ≤ n <1000 <br>

__Intuition ->Take the digits one by one , calculate sum of all cubes and compare.__<br>

```C++
string armstrongNumber(int n) {
        // code here
        int sum = 0;
        int k = n;
        
        while(n!=0){
            int digit = n%10;
            
            sum+= pow(digit,3);
            
            n = n /10;
        }
        
        return (sum==k)?"true":"false";
    }
```
