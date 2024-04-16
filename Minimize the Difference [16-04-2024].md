[Problem Link](https://www.geeksforgeeks.org/problems/minimize-the-difference/1)<br>
You are given an array arr of size n. You have to remove a subarray of size k , such that the difference between the maximum and minimum values of the remaining array is minimized.
Find the minimum value obtained after performing the operation of the removal of the subarray and return it.<br>

Example 1:<br>

Input:<br>
n = 5<br>
k = 3<br>
arr = {1, 2, 3, 4, 5}<br>
Output: 
1<br>
Explanation: 
We can remove first subarray of length 3(i.e. {1, 2, 3}) then remaining array will be {4,5} and the difference of maximum and minimum element will be 1 i.e 5 - 4 = 1<br>
Example 2:<br>

Input:<br>
n = 6<br>
k = 3<br>
arr = {2, 3, 1, 4, 6, 7}<br>
Output: 
2<br><br>
Explanation:<br>
If we remove the subarray {2,3,1} then remaining array will be {4,6,7} and the difference  = 7-4 = 3<br>
If we remove the subarray {3,1,4} then remaining array will be {2,6,7} and the difference  = 7-2 = 5<br>
If we remove the subarray {1,4,6} then remaining array will be {2,3,7} and the difference  = 7-2 = 5<br>
If we remove the subarray {4,6,7} then remaining array will be {2,3,1} and the difference  = 3-1 = 2<br>
So the answer will be min(3,5,5,2) = 2<br>
Your Task: 
You have to complete the function minimizeDifference( ), which takes two integers n and k and an integer array arr of size n. You have to return the minimum difference of maximum and minimum elements of the remaining array after removing one k length subarray of it.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
2 <= n <= 10^5<br>
1 <= k <= n-1<br>
0 <= arr[i] <= 10^9<br>

__Intuition -> Use two arrays post_max and post_min to keep track of max  and min element to the right of current index. Use two variables mini and maxi to keep track of max and min elements till the current index. Traverse and use these to find overall maximum and minimum elements after excluding the elements in the considered subarray.__

```C++
int minimizeDifference(int n, int k, vector<int> &arr) {
        // code here
        vector<int>post_max(n,0);
        vector<int>post_min(n,0);
        
        post_max[n-1]=arr[n-1];
        post_min[n-1]=arr[n-1];
        
        for(int i=n-2;i>=0;i--){
            post_max[i]=max(arr[i],post_max[i+1]);
            post_min[i]=min(arr[i],post_min[i+1]);
        }
        
        int ans  = post_max[k] - post_min[k];//for 1st subarray of size k
        
        int maxi = arr[0] , mini = arr[0];
        
        for(int i=1;i<n-k;i++){  //Going from 1st to n-1 subarray
        
            // cout<<i<<" "<<"maxi "<<maxi<<" mini "<<mini<<endl;
            ans = min(ans, max(post_max[i+k],maxi) - min(post_min[i+k],mini));
            
            maxi = max(arr[i],maxi);
            mini = min(arr[i],mini);
        }
        
        //for last subarray
        
        ans = min(ans , maxi-mini);
        return ans;
        
    }
```
