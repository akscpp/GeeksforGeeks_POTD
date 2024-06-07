[Problem Link](https://www.geeksforgeeks.org/problems/maximum-occured-integer4602/1)<br>

Given n integer ranges, the task is to return the maximum occurring integer in the given ranges. If more than one such integer exists, return the smallest one.<br>
The ranges are in two arrays l[] and r[].  l[i] consists of the starting point of the range and r[i] consists of the corresponding endpoint of the range & a maxx which is the maximum value of r[].<br>

For example, consider the following ranges.<br>
l[] = {2, 1, 3}, r[] = {5, 3, 9)<br>
Ranges represented by the above arrays are.<br>
[2, 5] = {2, 3, 4, 5}<br>
[1, 3] = {1, 2, 3}<br>
[3, 9] = {3, 4, 5, 6, 7, 8, 9}<br>
The maximum occurred integer in these ranges is 3.<br>

Examples :<br>

Input: n = 4, l[] = {1,4,3,1}, r[] = {15,8,5,4}, maxx = 15<br>
Output: 4<br>
Explanation: The given ranges are [1,15] [4, 8] [3, 5] [1, 4]. The smallest number that is most common or appears most times in the ranges is 4.<br>
Input: n = 5, l[] = {1,5,9,13,21}, r[] = {15,8,12,20,30}, maxx = 30<br>
Output: 5<br>
Explanation: The given ranges are [1, 15] [5, 8] [9, 12] [13, 20] [21, 30]. The smallest number that is most common or appears most times in the ranges is 5.<br>
Expected Time Complexity: O(n+maxx).<br>
Expected Auxiliary Space: O(maxx), maxx is maximum element in r[]<br>

Constraints:<br>
1 ≤ n ≤ 10^6<br>
0 ≤ l[i], r[i] ≤ 10^6<br>

__Intuition ->The code determines which number appears most frequently across multiple ranges by using a list to track the start and end of each range. It marks the beginning of a range with a +1 and just after the end with a -1. By cumulatively summing these values, it calculates the total number of ranges that cover each number. As it processes these cumulative sums, it keeps track of the number with the highest coverage, ultimately returning this number as the result.__

```C++
int maxOccured(int n, int l[], int r[], int maxx) {

        // Your code here
        vector<int>arr(maxx+2,0);
        
        for(int i=0;i<n;i++){
            arr[l[i]]++;
            arr[r[i]+1]--;
        }
        
        int maxi = arr[0],res = 0;
        
        for(int i=1;i<maxx+1;i++){
            arr[i]+=arr[i-1];
            
            if(maxi<arr[i]){
                maxi = arr[i];
                res= i;
            }
        }
        return res;
    }
```
