[Problem Link](https://www.geeksforgeeks.org/problems/max-sum-in-the-configuration/1)<br>
Given an integer array(0-based indexing) a of size n. Your task is to return the maximum value of the sum of i*a[i] for all 0<= i <=n-1, where a[i] is the element at index i in the array. The only operation allowed is to rotate(clockwise or counterclockwise) the array any number of times.<br>

Example 1:<br>

Input: n = 4, a[] = {8, 3, 1, 2}<br>
Output: 29<br>
Explanation: All the configurations possible by rotating the elements are:<br>
3 1 2 8 here sum is 3*0+1*1+2*2+8*3 = 29<br>
1 2 8 3 here sum is 1*0+2*1+8*2+3*3 = 27<br>
2 8 3 1 here sum is 2*0+8*1+3*2+1*3 = 17<br>
8 3 1 2 here sum is 8*0+3*1+1*2+2*3 = 11, so the maximum sum will be 29.<br>
Example 2:<br>

Input: n = 3, a[] = {1, 2, 3}<br>
Output: 8<br>
Explanation: All the configurations possible by rotating the elements are:<br>
1 2 3 here sum is 1*0+2*1+3*2 = 8<br>
3 1 2 here sum is 3*0+1*1+2*2 = 5<br>
2 3 1 here sum is 2*0+3*1+1*2 = 5, so the maximum sum will be 8.<br>
Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1<=n<=10^5<br>
1<=a[]<=10^6<br>

__Inuition ->The code efficiently finds the maximum weighted sum of an array for all its rotations by first calculating the initial weighted sum and total sum. For each rotation, it derives the new sum from the previous one by adjusting for the rotated elements, tracking the maximum sum encountered.__

```C++
long long max_sum(int arr[], int n) {
        // Your code here
        long long sum = 0;
        long long prev_sum = 0;
        
        for(int i=0;i<n;i++){
            prev_sum += (long long)i*arr[i];
            sum += arr[i];
        }
        
        long long ans = prev_sum;
        
        for(int i=1;i<n;i++){
            long long curr_sum = prev_sum - (sum - arr[i-1])+ (long long)arr[i-1]*(n-1);
            
            prev_sum = curr_sum;
            
            if(curr_sum >ans){
                ans = curr_sum;
            }
        }
        return ans;
    }
```

