[Problem Link](https://www.geeksforgeeks.org/problems/index-of-an-extra-element/1)<br>

You have given two sorted arrays arr1[] & arr2[] of distinct elements. The first array has one element extra added in between. Return the index of the extra element.<br>

Note: 0-based indexing is followed.<br>

Examples<br>

Input: n = 7, arr1[] = {2,4,6,8,9,10,12}, arr2[] = {2,4,6,8,10,12}<br>
Output: 4<br>
Explanation: In the first array, 9 is extra added and it's index is 4.<br>
Input: n = 6, arr1[] = {3,5,7,8,11,13}, arr2[] = {3,5,7,11,13}<br>
Output: 3<br>
Explanation: In the first array, 8 is extra and it's index is 3.<br>
Expected Time Complexity: O(log n).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1<=n<=10^5<br>
1<=arr1[i],arr2[i]<=10^6<br>

__Intuition ->Since the arrays are sorted, use binary search. If the value at mid is same in both the arrays , move low to mid+1 (Since arrays are sorted and there is only one extra extra element in first array, if values are same then the extra element must be in the right side of array). If the values are not equal ,move high to mid-1.__

```C++
int findExtra(int n, int arr1[], int arr2[]) {
        // add code here.
        int low = 0;
        int high = n - 2;
        
        while (low <= high){
            int mid = (low + high)/2;
            if (arr1[mid] == arr2[mid]){
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        
        return low;
    }
```
