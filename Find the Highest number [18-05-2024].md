[Problem Link](https://www.geeksforgeeks.org/problems/find-the-highest-number2259/1)<br>
Given an integer array a[] of size n, find the highest element of the array. The array will either be strictly increasing or strictly increasing and then strictly decreasing.<br>

Note: a[i] != a[i+1] <br>

Example 1:<br>

Input:
11<br>
1 2 3 4 5 6 5 4 3 2 1<br>
Output: 
6<br>
Explanation: 
Highest element of array a[] is 6.<br>
Example 2:<br>

Input:
5<br>
1 2 3 4 5<br>
Output:
5<br>
Explanation: 
Highest element of array a[] is 5.<br>
Your Task:
You don't need to read or print anything. Your task is to complete the function findPeakElement() which takes integer n, and the array a[] as the input parameters and returns the highest element of the array.<br>

Expected Time Complexity: O(log(n))<br>
Expected Space Complexity: O(1)<br>

Constraints:
2 <= n <= 10^6<br>
1 <= a[i] <= 10^6<br>

__Intuition ->Since the array is strictly increasing OR strictly increasing and then strictly decreasing, we can use binary search to find the greatest element.__

```C++
int findPeakElement(vector<int>& a) 
    {
        // Code here.
        int n = a.size();
        int l = 0,h = n-1;
        
        while(l<=h){
            int mid = (l+h)/2;
            if(mid==n-1) return a[mid];
            if(mid>0 && mid<n-1 && a[mid]>a[mid-1] && a[mid]>a[mid+1]){
                return a[mid];
            }else if(mid>0 && a[mid]>a[mid-1] || mid<n-1 && a[mid]<a[mid+1]){
                l=mid+1;
            }else h=mid-1;
        }
    }
```
