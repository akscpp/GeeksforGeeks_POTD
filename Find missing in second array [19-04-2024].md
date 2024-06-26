[Problem Link](https://www.geeksforgeeks.org/problems/in-first-but-second5423/1)<br>

Given two integer arrays a of size n and b of size m, the task is to find the numbers which are present in the first array a, but not present in the second array b.<br>

Example 1:<br>

Input: <br>
n = 6, m = 5<br>
a[] = {1, 2, 3, 4, 5, 10}<br>
b[] = {2, 3, 1, 0, 5}<br>
Output: <br>
4 10<br>
Explanation: <br>
4 and 10 are present in first array, but not in second array.<br>
Example 2:<br>

Input:<br> 
n = 5, m = 5<br>
a[] = {4, 3, 5, 9, 11}<br>
b[] = {4, 9, 3, 11, 10}<br>
Output: 
5  <br>
Explanation: <br>
Second array does not contain element 5.<br>
Your Task:<br>
You don't need to take any input, as it is already accomplished by the driver code. You just need to complete the function findMissing() that takes an integer array a, an integer array b, an integer n, and an integer m as input parameters and returns an array that contains the missing elements and the order of the elements should be the same as they are in array a.<br>

Expected Time Complexity: O(n+m).<br>
Expected Auxiliary Space: O(m).<br>

Constraints:<br>
1 ≤ n, m ≤ 10^5<br>
-10^9 ≤ A[i], B[i] ≤ 10^9<br>

__Intuition -> Use set. Keep all elements are array b in set. Traverse array a and find if the element is present in set or not.__

```C++
vector<int> findMissing(int a[], int b[], int n, int m) 
	{ 
	    // Your code goes here
	    unordered_set<int>s;
	    
	    for(int i=0;i<m;i++){
	        s.insert(b[i]);
	    }
	    
	    vector<int>ans;
	    for(int i=0;i<n;i++){
	        if(s.find(a[i])==s.end()){
	            ans.push_back(a[i]);
	        }
	    }
	    return ans;
	} 
```
