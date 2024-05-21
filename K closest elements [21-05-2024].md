[Problem Link](https://www.geeksforgeeks.org/problems/k-closest-elements3619/1)<br>
Given a sorted array of unique elements in increasing order, arr[] of n integers, and a value x. Find the K closest elements to x in arr[].<br>
Keep the following points in mind:<br>

If x is present in the array, then it need not be considered.<br>
If two elements have the same difference as x, the greater element is prioritized.<br>
If sufficient elements are not present on the right side, take elements from the left and vice versa.<br>
 
Example 1:<br>

Input:
n = 13<br>
arr[] = {12, 16, 22, 30, 35, 39, 42, 
         45, 48, 50, 53, 55, 56}<br>
k = 4, x = 35<br>
Output: 39 30 42 45<br>
Explanation: <br>
First closest element to 35 is 39.<br>
Second closest element to 35 is 30.<br>
Third closest element to 35 is 42.<br>
And fourth closest element to 35 is 45.<br>

Example 2:<br>

Input:
n = 5<br>
arr[] = {1, 2, 3, 6, 10}<br>
k = 3, x = 4<br>
Output: 3 6 2<br>
Explanation: <br>
First closest element is 3.<br>
There are two elements 2 and 6 for which 
the difference with 4 is same i.e. 2.
So first take greatest number 6 
then the lower number 2.<br>

Your Task:
You don't need to read input or print anything. Complete the function printKClosest() which takes arr[], n, k, and x as input parameters and returns an array of integers containing the K closest elements to x in arr[].<br>


Expected Time Complexity: O(log n + k)<br>
Expected Auxiliary Space: O(k)<br>


Constraints:<br>
1 ≤ n ≤ 10^5<br>
1 ≤ k ≤ n<br>
1 ≤ x ≤ 10^6<br>
1 ≤ arr[i] ≤ 10^6<br>

__Intuition ->Since the array is sorted , the first thought should be of binary search. Find the closest element to x using binary search. Also , handle the base cases where arr[low]> x or arr[high]<x. Once we get the closest element , starting filling the answer array based on the given conditions in the question.__

```C++
int findClosest(vector<int>&arr,int low,int high,int x){
        while(low<=high){
            
            if(arr[high]<=x){
                return high;
            }
            
            if(arr[low]>x){
                return low;
            }
            
            int mid = low + (high-low)/2;
            
            if(arr[mid]<=x && arr[mid+1]>x){
                return mid;
            }
            
            if(arr[mid]>x){
                high = mid-1;
            }else{
                low = mid+1;
            }
        }
        return -1;
    }
    vector<int> printKClosest(vector<int> arr, int n, int k, int x) {
        
        vector<int>ans(k,0);
        int m = 0;
        int l = findClosest(arr,0,n-1,x);
        int r = l+1;
        
        if(arr[l]==x){
            l--;
        }
        
        while(l>=0 && r<n && m<k){
            if(x-arr[l] < arr[r]-x){
                ans[m++] = arr[l];
                l--;
            }else{
                ans[m++]=arr[r];
                r++;
            }
        }
        
        while(m<k && l>=0){
            ans[m++] = arr[l];
                l--;
        }
        
        while(m<k && r<n){
            ans[m++]=arr[r];
                r++;
        }
        
        return ans;
    }
```
