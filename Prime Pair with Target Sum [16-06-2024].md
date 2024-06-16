[Problem Link](https://www.geeksforgeeks.org/problems/sum-of-prime4751/1)<br>

Given a number n, find out if n can be expressed as a+b, where both a and b are prime numbers. If such a pair exists, return the values of a and b, otherwise return [-1,-1] as an array of size 2.
Note: If [a, b] is one solution with a <= b, and [c, d] is another solution with c <= d, and a < c then  [a, b] is considered as our answer.<br>

Examples<br>

Input: n = 10<br>
Output: 3 7<br>
Explanation: There are two possiblities 3, 7 & 5, 5 are both prime & their sum is 10, but we'll pick 3, 7 as 3 < 5.<br>
Input: n = 3<br>
Output: -1 -1<br>
Explanation: There are no solutions to the number 3.<br>
Expected Time Complexity: O(n*loglog(n))<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
2 <= n <= 10^6<br>

__Intuition ->Use Sieve of Eratosthenes to find all prime numbers till n. Now , traverse from 2 to n and find if i and n-i are prime or not. If both are prime , return them. If no such pair exists, return {-1,-1}.__

```C++
vector<int> getPrimes(int n) {
        // code here
        vector<bool>seive(n+1,true);
        seive[0]=false;
        seive[1]=false;
        
        for(int i=2;i<=n;i++){
            if(seive[i]==true){
                for(int j = i*2;j<=n;j+=i){
                    seive[j]=false;
                }
            }
        }
        
        for(int i=2;i<=n;i++){
            if(seive[i]==true && seive[n-i]==true){
                return {i,n-i};
            }
        }
        return {-1,-1};
    }
```
