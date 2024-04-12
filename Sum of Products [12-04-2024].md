[Problem Link](https://www.geeksforgeeks.org/problems/sum-of-products5049/1)<br>
Given an array arr[] of size n. Calculate the sum of Bitwise ANDs ie: calculate sum of arr[i] & arr[j] for all the pairs in the given array arr[] where i < j.<br>

Example 1:<br>

Input:
n = 3<br>
arr = {5, 10, 15}<br>
Output:
15<br>
Explanation:
The bitwise Ands of all pairs where i<j are (5&10) = 0, (5&15) = 5 and (10&15) = 10.
Therefore, the total sum = (0+5+10) = 15.<br>
Example 2:<br>

Input:
n = 4<br>
arr = {10, 20, 30, 40}<br>
Output:
46<br>
Explanation:
The sum of bitwise Ands 
of all pairs = (0+10+8+20+0+8) = 46.<br>
Your Task:<br>
You don't need to read input or print anything.Your Task is to complete the function pairAndSum() which takes an Integer n and an array arr[]  of size n as input parameters and returns the sum of bitwise Ands of all pairs.<br>

Expected Time Complexity:O(n)<br>
Expected Auxillary Space:O(1)<br>

Constraints:<br>
1 <= n <= 10^5<br>
1 <= arr[i] <= 10^8<br>

__Intuition->Since the question demands linear time complexity , generating all possible pairs using nested loops or merge sort will give TLE. Another approach is to count the no. of set bits of all the elements of the array at a position. Then use combination to calculate no. of pairs nC2.__

```C++
long long pairAndSum(int n, long long arr[]) {
        // code here
        long long int ans = 0;
        
        for(int i=0;i<32;i++){
            long long  int cnt = 0;
            
            long long int k = (1 << i);   //Traversing through different bits
            
            for(int j=0;j<n;j++){
                
                if(arr[j] & k){           //If bit is set at kth bit , increase the count
                    cnt++;
                }
            }
            
            ans+= (cnt*(cnt-1))/2 * (k);              //counting total no. of pairs having set bit at kth bit
        }
        return ans;
    }
```
