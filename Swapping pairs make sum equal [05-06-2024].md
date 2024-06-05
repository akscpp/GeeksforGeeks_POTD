[Problem Link](https://www.geeksforgeeks.org/problems/swapping-pairs-make-sum-equal4142/1)<br>
Given two arrays of integers a[] and b[] of size n and m, the task is to check if a pair of values (one value from each array) exists such that swapping the elements of the pair will make the sum of two arrays equal.<br>

Note: Return 1 if there exists any such pair otherwise return -1.<br>

Example 1:<br>

Input: n = 6, m = 4, a[] = {4, 1, 2, 1, 1, 2}, b[] = (3, 6, 3, 3)<br>
Output: 1<br>
Explanation: Sum of elements in a[] = 11, Sum of elements in b[] = 15, To get same sum from both arrays, we can swap following values: 1 from a[] and 3 from b[]<br>
Example 2:<br>

Input: n = 4, m = 4, a[] = {5, 7, 4, 6}, b[] = {1, 2, 3, 8}<br>
Output: 1<br>
Explanation: We can swap 6 from array a[] and 2 from array b[]<br>
Expected Time Complexity: O(mlogm+nlogn).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1 ≤ n, m ≤ 10^6<br>
0 <= a[i], b[i] <= 10^5<br>

__Intuition ->Sort both the arrays. Then use two pointers approach to compare sum of both array after adding and subtacting the swapped element. If the sum is equal , return 1. If the sum1 (sum of array 1 after modification) is greater than sum2 , this means that we have to add a greater element to the second array to compete with the sum1. SO , do i++. Else j++ (on second array).__

```C++
int findSwapValues(int a[], int n, int b[], int m) {
        // Your code goes here
        
        sort(a,a+n);
        sort(b,b+m);
        
        int s1 = 0;
        int s2 = 0;
        
        for(int i=0;i<n;i++){
            s1+=a[i];
        }
        
        for(int i=0;i<m;i++){
            s2+=b[i];
        }
        
        int i=0,j=0;
        
        while(i<n && j<m){
            int sum1 = s1 - a[i] + b[j];
            int sum2 = s2 - b[j] + a[i];
            
            if(sum1==sum2) return 1;
            else if(sum1>sum2) i++;
            else j++;
        }
        
        return -1;
    }
```
