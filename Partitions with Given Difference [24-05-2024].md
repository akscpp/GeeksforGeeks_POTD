[Problem Link](https://www.geeksforgeeks.org/problems/partitions-with-given-difference/1)<br>
Given an array arr, partition it into two subsets(possibly empty) such that each element must belong to only one subset. Let the sum of the elements of these two subsets be S1 and S2. <br>
Given a difference d, count the number of partitions in which S1 is greater than or equal to S2 and the difference between S1 and S2 is equal to d. Since the answer may be large return it modulo 10^9 + 7.<br>

Example 1:<br>

Input:
n = 4<br>
d = 3<br>
arr[] =  { 5, 2, 6, 4}<br>
Output: 1<br>
Explanation:<br>
There is only one possible partition of this array. Partition : {6, 4}, {5, 2}. The subset difference between subset sum is: (6 + 4) - (5 + 2) = 3.<br>
Example 2:<br>

Input:
n = 4<br>
d = 0 <br>
arr[] = {1, 1, 1, 1} <br>
Output: 6 <br>
Explanation:
we can choose two 1's from indices {0,1}, {0,2}, {0,3}, {1,2}, {1,3}, {2,3} and put them in S1 and remaning two 1's in S2.
Thus there are total 6 ways for partition the array arr. <br>
Your Task:
You don't have to read input or print anything. Your task is to complete the function countPartitions() which takes the integer n and d and array arr and returns the count of partitions.<br>

Expected Time Complexity: O( n*sum(arr))<br>
Expected Space Complexity: O( sum(arr))<br>

Constraint:
1 <= n <= 500<br>
0 <= d  <= 25000<br>
0 <= arr[i] <= 50<br>

__Intuition->This question can be converted to find the count of subsets with sum k.__ <br>
__S1 + S2 = totalSum__ <br>
__S1 - S2 = d__ <br>
__S1 = (d + totalSum)/2 = k__ <br>

```C++
const int MOD = 1e9+7;
    vector<vector<int>> dp;
    
    int fun(int ind, int sum, vector<int>& arr) {
        if (ind == 0) {
            if (arr[ind] == 0 && sum == 0) return 2; 
            if (sum == 0 || arr[ind] == sum) return 1;
            return 0;
        }
        
        if (dp[ind][sum] != -1) return dp[ind][sum];
        
        int Take = 0;
        if (sum - arr[ind] >= 0) {
            Take = fun(ind - 1, sum - arr[ind], arr);
        }
        
        int nTake = fun(ind - 1, sum, arr);
        
        return dp[ind][sum] = (Take + nTake) % MOD;
    }
    
    int countPartitions(int n, int d, vector<int>& arr) {
        int totalSum = 0;
        for (int i = 0; i < n; i++) {
            totalSum += arr[i];
        }
        
        
        if ((totalSum + d) % 2 != 0) return 0;
        int target = (totalSum + d) / 2;
        
        
        dp = vector<vector<int>>(n, vector<int>(target + 1, -1));
        
        return fun(n - 1, target, arr) % MOD;
    }
```
