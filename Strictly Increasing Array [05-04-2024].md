[Problem Link](https://www.geeksforgeeks.org/problems/convert-to-strictly-increasing-array3351/1)<br>
Given an array nums of n positive integers. Find the minimum number of operations required to modify the array such that array elements are in strictly increasing order (nums[i] < nums[i+1]).
Changing a number to greater or lesser than original number is counted as one operation.<br>

Note: Array elements can become negative after applying operation.<br>

Example 1:<br>

Input:
n = 6<br>
nums = [1, 2, 3, 6, 5, 4]<br>
Output: 
2<br>
Explanation: 
By decreasing 6 by 2 and increasing 4 by 2, nums will be like [1, 2, 3, 4, 5, 6] which is stricly increasing.<br>
Example 2:<br>

Input: 
n = 4<br>
nums = [1, 1, 1, 1]<br>
Output: 
3<br>
Explanation: 
One such array after operation can be [-2, -1, 0, 1]. We require atleast 3 operations for this example.<br>
Your Task:
You don't need to read or print anything. Your task is to complete the function min_opeartions() which takes the array nums as input parameter and returns the minimum number of opeartion needed to make the array strictly increasing.<br>

Expected Time Complexity: O(n^2)<br>
Expected Space Complexity: O(n)<br>

Constraints: <br>
1 <= n <= 10^3<br>
1 <= nums[i] <= 10^9<br>

__Intuition -> Find the length of largest increasing subsequence and subract it from the length of array. This gives the no. of elements that need to be ooperated in order to make the whole array strictly increasing.__

```C++
int LIS(vector<int>& nums){
        int len=0;
        int n = nums.size();
        vector<int>dp(n,1);
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[i]>nums[j] && nums[i]-nums[j]>=i-j){
                    dp[i]=max(dp[i],1+dp[j]);
                }
            }
        }
        
        for(auto it:dp){
            len=max(len,it);
        }
        return len;
    }
    int min_operations(vector<int>& nums) {
        // Code here
        int l = LIS(nums);
        
        return nums.size()-l;
    }
```
