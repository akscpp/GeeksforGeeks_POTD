[Problem Link](https://www.geeksforgeeks.org/problems/three-sum-closest/1)<br>
Given an array, arr of integers, and another number target, find three integers in the array such that their sum is closest to the target. Return the sum of the three integers.<br>

Note: If there are multiple solutions, return the maximum one.<br>

Examples :<br>

Input: arr[] = [-7, 9, 8, 3, 1, 1], target = 2<br>
Output: 2<br>
Explanation: There is only one triplet present in the array where elements are -7,8,1 whose sum is 2.<br>
Input: arr[] = [5, 2, 7, 5], target = 13<br>
Output: 14<br>
Explanation: There is one triplet with sum 12 and other with sum 14 in the array. Triplet elements are 5, 2, 5 and 2, 7, 5 respectively. Since abs(13-12) ==abs(13-14) maximum triplet sum will be preferred i.e 14.<br>
Expected Time Complexity: O(n^2)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
3 ≤ arr.size() ≤ 10^3<br>
-105 ≤ arr[i] ≤ 10^5<br>
1 ≤ target ≤ 10^5

__Intuition -> Sort the array and use the concept of three sum. Use a variable to track the closest sum.__

```C++
int threeSumClosest(vector<int> arr, int target) {
        std::sort(arr.begin(), arr.end());
        int n = arr.size();
        int closestSum = INT_MAX;
        int resultSum = 0;

        for (int i = 0; i < n - 2; ++i) {
            int left = i + 1;
            int right = n - 1;

            while (left < right) {
            int currentSum = arr[i] + arr[left] + arr[right];
            
            if (std::abs(target - currentSum) < std::abs(target - closestSum)) {
                closestSum = currentSum;
                resultSum = currentSum;
            } else if (std::abs(target - currentSum) == std::abs(target - closestSum)) {
               resultSum = std::max(resultSum, currentSum);
            }

            if (currentSum < target) {
                ++left;
            } else {
                --right;
            }
        }
    }

        return resultSum;
    }
```
