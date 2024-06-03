[Problem Link](https://www.geeksforgeeks.org/problems/trail-of-ones3242/1)<br>
Given a number n, find the number of binary strings of length n that contain consecutive 1's in them. Since the number can be very large, return the answer after modulo with 1e9+7.<br>

Example 1:<br>

Input:
n = 2<br>
Output:
1<br>
Explanation:
There are 4 strings of 
length 2, the strings 
are 00, 01, 10, and 
11. Only the string 11 
has consecutive 1's.<br>
Example 2:<br>

Input:
n = 5<br>
Output:
19<br><br>
Explanation:
There are 19 strings
having consecutive 1's.
Your Task:

You don't need to read input or print anything. Your task is to complete the function numberOfConsecutiveOnes() which takes an integer n and returns the number of binary strings that contain consecutive 1's in them.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints
2 <= n <= 10^5<br>

__Intuition ->Find the number of binary strings not having consecutive ones and subtract it from total number of binary strings for n.We can append 1 or 0 if the previous element is 0. But if the previous element is 1 , we can only append 0. (to avoid consecutive 1s).__

```C++
int MOD = 1e9+7;
    long long power(long long a , long long b){
        long long ans = 1;
        
        while(b>0){
            if(b&1){
                ans*=a;
                ans%=MOD;
            }
            
            a*=a;
            a%=MOD;
            b >>=1;
        }
        return ans;
        
    }
    int numberOfConsecutiveOnes(int n) {
        // code here
        vector<int>a(n);
        vector<int>b(n);
        
        a[0]=1;
        b[0]=1;
        
        for(int i =1;i<n;i++){
            a[i]=(a[i-1]+b[i-1])%MOD;
            b[i]=a[i-1];
        }
        
        return (power(2,n)+MOD - (a[n-1]+b[n-1])%MOD)%MOD;
    }
```
