Given two sorted matrices mat1 and mat2 of size n x n of elements. Each matrix contains numbers arranged in strictly ascending order, with each row sorted from left to right, and the last element of a row being smaller than the first element of the next row. You're given a target value, x, your task is to find and count all pairs {a, b} such that a is from mat1 and b is from mat2 where sum of a and b is equal to x.<br>

Example 1:<br>

Input: 
n = 3, x = 21<br>
mat1 = {{1, 5, 6},
        {8, 10, 11},
        {15, 16, 18}}<br>
mat2 = {{2, 4, 7},
        {9, 10, 12},
        {13, 16, 20}}<br>
OUTPUT: 4<br>
Explanation: The pairs whose sum is found to be 21 are (1, 20), (5, 16), (8, 13), (11, 10).<br>
Example 2:<br>

Input:
n = 2, x = 10<br>
mat1 = {{1, 2},
        {3, 4}}<br>
mat2 = {{4, 5},
        {6, 7}}<br>
Output: 2<br>
Explanation: The pairs whose sum found to be 10 are (4, 6), (3, 7).<br>
User Task:
Your task is to complete the function countPairs() which takes 4 arguments mat1, mat2, n, x, and returns the count of pairs whose sum equals to x. You don't need to take any input or print anything.<br>

Expected Time Complexity: O(n^2).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1 ≤ mat1[i][j] , mat2[i][j] ≤ 10^5<br>
1 ≤ n ≤ 100<br>
1 ≤ x ≤ 10^5<br>


__Intuition -> Traverse through one matrix and find the value of x-mat1[i][j] in another matrix using binary search.__

```C++
bool find(vector<vector<int>> &mat2 , int x){
        int n = mat2.size();
        int start=0,end=n-1;
        while(start<n && end>=0){
            if(mat2[start][end]==x){
                return true;
            }
            if(mat2[start][end]<x){
                start++;
            }else end--;
        }
        return false;
    }
	
	int countPairs(vector<vector<int>> &mat1, vector<vector<int>> &mat2, int n, int x)
	{
	    // Your code goes here
	    int cnt=0;
	    for(int i=0;i<n;i++){
	        for(int j=0;j<n;j++){
	            if(find(mat2,x-mat1[i][j])){
	                cnt++;
	            }
	        }
	    }
	    return cnt;
	    
	    
	    
	}
```
