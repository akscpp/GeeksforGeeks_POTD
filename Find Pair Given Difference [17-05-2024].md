[Problem Link](https://www.geeksforgeeks.org/problems/find-pair-given-difference1559/1)<br>
Given an array arr[] of size n and an integer x, return 1 if there exists a pair of elements in the array whose absolute difference is x, otherwise, return -1.<br>

Example 1:<br>

Input:<br>
n = 6<br>
x = 78<br>
arr[] = {5, 20, 3, 2, 5, 80}<br>
Output:
1<br>
Explanation:
Pair (2, 80) have absolute difference of 78.<br>
Example 2:<br>

Input:
n = 5<br>
x = 45<br>
arr[] = {90, 70, 20, 80, 50}<br>
Output:
-1<br>
Explanation:
There is no pair with absolute difference of 45.<br>
Your Task:
You need not take input or print anything. Your task is to complete the function findPair() which takes integers n, x, and an array arr[] as input parameters and returns 1 if the required pair exists, return -1 otherwise.<br>

Expected Time Complexity: O(n* Log(n)).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1<=n<=10^6 <br>
1<=arr[i]<=1^06 <br>
0<=x<=10^5<br>

__Intuition ->Sort the array and use two pointers to find the pair whose absolute difference is x.__

```C++
int findPair(int n, int x, vector<int> &arr) {
        // code here
        int i = 0, j=i+1;
        sort(begin(arr),end(arr));
        while(j<n){
            int diff = abs(arr[i]-arr[j]);
            
            if(diff==x) return 1;
            else if (diff>x) i++;
            else j++;
            
            if(i==j) j++;
        }
        
        return -1;
    }
```
