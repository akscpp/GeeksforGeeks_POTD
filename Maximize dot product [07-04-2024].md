[Problem Link](https://www.geeksforgeeks.org/problems/maximize-dot-product2649/1)<br>
Given two arrays a and b of positive integers of size n and m where n >= m, the task is to maximize the dot product by inserting zeros in the second array but you cannot disturb the order of elements.<br>

Dot product of array a and b of size n is a[0]*b[0] + a[1]*b[1] + ... + a[n-1]*b[n-1].<br>

Example 1:<br>

Input: 
n = 5, a[] = {2, 3, 1, 7, 8} <br>
m = 3, b[] = {3, 6, 7}<br>
Output: <br>
107<br>
Explanation: 
We get maximum dot product after inserting 0 at first and third positions in second array.
Therefore b becomes {0, 3, 0, 6, 7}. <br>
Maximum dot product = 2*0 + 3*3 + 1*0 + 7*6 + 8*7 = 107.<br>
Example 2:<br>

Input: 
n = 3, a[] = {1, 2, 3}<br><br>
m = 1, b[] = {4} 
Output: 
12 <br>
Explanation: 
We get maximum dot product after inserting 0 at first and second positions in second array.<br>
Therefore b becomes {0, 0, 4}. <br>
Maximum Dot Product = 1*0 + 2*0 + 3*4 = 12.<br>
Your Task:  
You don't need to read input or print anything. Complete the function maxDotProduct() which takes n, m, array a and b as input parameters and returns the maximum value.<br>

Expected Time Complexity: O(n*m)<br>
Expected Auxiliary Space: O(n*m)<br>

Constraints:<br>
1 ≤ m ≤n ≤ 10^3<br>
1 ≤ a[i], b[i] ≤ 10^3<br>

__Intuition -> Since we have option whether to take 0 or the element , we will go with recursion. Also , at max n-m no. of 0's can be used.__

```C++
int solve(int i,int j,int n, int m, int a[], int b[],vector<vector<int>>&dp,int gap){
	    if(i<0 || j<0){
	        return 0;
	    }
	    if(dp[i][j]!=-1) return dp[i][j];
	    
	    int take = a[i]*b[j] + solve(i-1,j-1,n,m,a,b,dp,gap);
	    
	    int ntake = 0;
	    if(gap>0){
	        ntake = 0 + solve(i-1,j,n,m,a,b,dp,gap-1);
	    }
	    return dp[i][j]=max(take,ntake);
	}
	int maxDotProduct(int n, int m, int a[], int b[]) 
	{ 
		// Your code goes here
		vector<vector<int>>dp(n+1,vector<int>(m+1,-1));
		int gap = n-m;
		return solve(n-1,m-1,n,m,a,b,dp,gap);
	} 
```
