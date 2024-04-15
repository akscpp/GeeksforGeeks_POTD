[Problem Link](https://www.geeksforgeeks.org/problems/count-the-elements1529/1)<br>

Given two arrays a and b both of size n. Given q queries in an arrray query each having a positive integer x denoting an index of the array a. For each query, your task is to find all the elements less than or equal to a[x] in the array b.<br>

Example 1:<br>

Input:<br>
n = 3<br>
a[] = {4,1,2}<br>
b[] = {1,7,3}<br>
q = 2<br>
query[] = {0,1}<br>
Output : <br>
2<br>
1<br>
Explanation: <br>
For 1st query, the given index is 0, a[0] = 4. There are 2 elements(1 and 3) which are less than or equal to 4.<br>
For 2nd query, the given index is 1, a[1] = 1. There exists only 1 element(1) which is less than or equal to 1.<br>
Example 2:<br>

Input:<br>
n = 4<br>
a[] = {1,1,5,5}<br>
b[] = {0,1,2,3}<br>
q = 4<br>
query[] = {0,1,2,3}<br>
Output : <br>
2<br>
2<br>
4<br>
4<br>
Explanation: <br>
For 1st query and 2nd query, the given index is 0 and 1 respectively, a[0] = a[1] = 1. There are 2 elements(0 and 1) which are less than or equal to 1. <br>
For 3rd query and 4th query, the given index is 2 and 3 respectively, a[2] = a[3] = 5. All the 4 elements are less than or equal to 5. <br>  
Your Task:<br>
You don't need to take any input, as it is already accomplished by the driver code. You just need to complete the function countElements() that takes array a and b of size n, and array query of size q as parameters and returns an array that contains the answer to the corresponding queries. <br>

__Intuition -> Maintain a hash array. Use that to store count of elements of b. Now , to store count of elements less than or equal to current element , add the previous count to current count while iterating through the hash count array. At last , iterate over the query array and find the count of elements less than or equal to current index element.__

```C++
vector<int> countElements(vector<int> &a, vector<int> &b, int n, vector<int> &query,
                              int q) {
        // Your code goes here;
        
        int maxi = -1e9;
        for(int i=0;i<n;i++){
            maxi = max(a[i],maxi);
        }
        for(int i=0;i<n;i++){
            maxi = max(b[i],maxi);
        }
        
        vector<int>cnt(maxi+1,0);
        for(int i=0;i<n;i++){
            cnt[b[i]]++;
        }
        
        for(int i=1;i<=maxi;i++){
            cnt[i]+=cnt[i-1];
        }
        
        vector<int>ans;
        for(int i=0;i<q;i++){
            ans.push_back(cnt[a[query[i]]]);
        }
        return ans;
    }
```

Expected Time Complexity: O(n+q).
Expected Auxiliary Space: O(maximum of a and b).

Constraints:
1 ≤ q ≤ n ≤ 105
1 ≤ a[i], b[i] ≤ 105
0 ≤ query[i] < n
