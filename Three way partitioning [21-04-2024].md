[Problem Link](https://www.geeksforgeeks.org/problems/three-way-partitioning/1)<br>
Given an array of size n and a range [a, b]. The task is to partition the array around the range such that the array is divided into three parts.<br>
1) All elements smaller than a come first.<br>
2) All elements in range a to b come next.<br>
3) All elements greater than b appear in the end.<br>
The individual elements of three sets can appear in any order. You are required to return the modified array.<br>

Note: The generated output is 1 if you modify the given array successfully.<br>

Geeky Challenge: Solve this problem in O(n) time complexity.<br>

Example 1:<br>

Input:<br> 
n = 5<br>
array[] = {1, 2, 3, 3, 4}<br>
[a, b] = [1, 2]<br>
Output: 
1<br>
Explanation: <br>
One possible arrangement is: {1, 2, 3, 3, 4}. If you return a valid arrangement, output will be 1.<br>
Example 2:<br>

Input: <br>
n = 6 <br>
array[] = {1, 4, 3, 6, 2, 1}<br>
[a, b] = [1, 3]<br>
Output: <br>
1<br>
Explanation: <br>
One possible arrangement is: {1, 3, 2, 1, 4, 6}. If you return a valid arrangement, output will be 1.<br>
Your Task:<br>
You don't need to read input or print anything. The task is to complete the function threeWayPartition() which takes the array array, a, and b as input parameters and modifies the array in place according to the given conditions.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 <= n <= 10^6<br>
1 <= array[i], a, b <= 10^9<br>

__Intuition ->Use DNF (Dutch National Flag Algorithm). Use three pointers to partition the array into 3 parts.__

```C++
void threeWayPartition(vector<int>& arr,int a, int b)
    {
        // code here 
        int n = arr.size();
        int low=0,mid=0,high=n-1;
        
        while(mid<=high){
            if(arr[mid]<a){
                swap(arr[low],arr[mid]);
                low++;mid++;
            }else if(arr[mid]>=a && arr[mid]<=b){
                mid++;
            }else{
                swap(arr[mid],arr[high]);
                high--;
            }
        }
        
    }
```
