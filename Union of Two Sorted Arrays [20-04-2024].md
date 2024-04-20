[Problem Link](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1)<br>
Given two sorted arrays of size n and m respectively, find their union. The Union of two arrays can be defined as the common and distinct elements in the two arrays. <br>

Example 1:<br>

Input: <br>
n = 5, arr1[] = {1, 2, 3, 4, 5}  <br>
m = 5, arr2 [] = {1, 2, 3, 6, 7}<br>
Output: <br>
1 2 3 4 5 6 7<br>
Explanation: <br>
Distinct elements including both the arrays are: 1 2 3 4 5 6 7.<br>
Example 2:<br>

Input:<br> 
n = 5, arr1[] = {2, 2, 3, 4, 5}  <br>
m = 5, arr2[] = {1, 1, 2, 3, 4}<br>
Output: <br>
1 2 3 4 5<br>
Explanation: <br>
Distinct elements including both the arrays are: 1 2 3 4 5.<br>
Example 3:<br>

Input:<br>
n = 5, arr1[] = {1, 1, 1, 1, 1}<br>
m = 5, arr2[] = {2, 2, 2, 2, 2}<br>
Output: <br>
1 2<br>
Explanation: <br>
Distinct elements including both the arrays are: 1 2.<br>
Your Task: <br>
You do not need to read input or print anything. Complete the function findUnion() that takes two arrays arr1[], arr2[], and their size n and m as input parameters and returns a list containing the union of the two arrays.<br>

Expected Time Complexity: O(n+m).<br>
Expected Auxiliary Space: O(n+m).<br>

Constraints:<br>
1 <= n, m <= 10^5<br>
-10^9 <= arr1[i], arr2[i] <= 10^9<br>

__Intuition-> Traverse both the arrays simultaneously. If current element is same as previous element , don't include it in answer. In every other case , include it in the answer. Also, while including the element in the answer, compare the two elements of the arrays to maintain the sorted order.__

```C++
vector<int> findUnion(int arr1[], int arr2[], int n, int m)
    {
        //Your code here
        //return vector with correct order of elements
        vector<int>ans;
        int i = 0, j=0;
        
        while(i<n && j<m){
            if(i>0 && arr1[i]==arr1[i-1]) {
                i++;continue;
            }
            if(j>0 && arr2[j]==arr2[j-1]) {
                j++;continue;
            }
            
            if(arr1[i]==arr2[j]){
                ans.push_back(arr1[i]);
                i++;j++;
                
            }else if(arr1[i]<arr2[j]){
                ans.push_back(arr1[i]);i++;
            }else {
                ans.push_back(arr2[j]);j++;
            }
        }
        
        while(i<n){
            if(i>0 && arr1[i]==arr1[i-1]) {
                i++;
            }else{
                ans.push_back(arr1[i]);
                i++;
            }
        }
        while(j<m){
            if(j>0 && arr2[j]==arr2[j-1]) {
                j++;
            }else{
                ans.push_back(arr2[j]);
                j++;
            }
        }
        return ans;
    }
```
