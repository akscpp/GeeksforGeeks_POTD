[Problem Link](https://www.geeksforgeeks.org/problems/find-the-closest-number5513/1)<br>

Given a sorted array arr[] of positive integers. The task is to find the closest value in the array to the given number k. The array may contain duplicate values.<br>

Note: If the difference with k is the same for two values in the array return the greater value.<br>

Example 1:.<br>

Input: 
n = 4<br>
k = 4<br>
arr[] = {1, 3, 6, 7}<br>
Output: 
3<br>
Explanation:
We have array arr={1, 3, 6, 7} and target is 4. If we look at the absolute difference of target with every element of the array we will get { |1-4|, |3-4|, |6-4|, |7-4| }  = {3, 1, 2, 3}. So, the closest number is 3.<br>
Example 2:<br>

Input:
n = 7<br>
k = 4<br>
arr[] = {1, 2, 3, 5, 6, 8, 9}<br>
Output:
5<br>
Explanation:
The absolute difference of 4 is 1 from both 3 and 5. According to the question, we have to return greater value, which is 5.<br>
Your Task:
This is a function problem. The input is already taken care of by the driver code. You only need to complete the function findClosest() that takes integers n and k and sorted array arr[] of size n as input parameters and return the closest number in the array to k. <br>

Expected Time Complexity: O(log(n)).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:
1 ≤ n ≤ 10^6<br>
1 ≤ k ≤ 10^9<br>
1 ≤ arr[i] ≤ 10^9<br>

__Intuition ->Use binary search. Find the minimum difference.__

```C++
int findClosest( int n, int k,int arr[]) 
    { 
        // Complete the function
        int low = 0 , high = n-1 , ans = arr[0];
        
        while(low<=high){
            int mid = (low+high)/2;
            
            if(abs(ans-k)==abs(k-arr[mid])){
                
                ans = max(ans,arr[mid]);
                
            }else if(abs(k-arr[mid])<abs(k-ans)){
                
                ans = arr[mid];
            }
            
            
            if(arr[mid]==k){
                return arr[mid];
            }else if(arr[mid]<k){
                low = mid+1;
            }else high = mid-1;

        }
        return ans;
    } 
```
