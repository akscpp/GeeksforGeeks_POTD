[Problem Link](https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1)<br>

Given a boolean 2D array, consisting of only 1's and 0's, where each row is sorted. Return the 0-based index of the first row that has the most number of 1s. If no such row exists, return -1.<br>

Examples:<br>

Input: arr[][] = [[0, 1, 1, 1],<br>
               [0, 0, 1, 1],<br>
               [1, 1, 1, 1],<br>
               [0, 0, 0, 0]]<br>
Output: 2<br>
Explanation: Row 2 contains 4 1's (0-based indexing).<br>
Input: arr[][] = [[0, 0], <br>
               [1, 1]]<br>
Output: 1<br>
Explanation: Row 1 contains 2 1's (0-based indexing).<br>
Expected Time Complexity: O(n+m)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 ≤ number of rows, number of columns ≤ 10^3<br>
0 ≤ arr[i][j] ≤ 1 <br>

__Intuition ->Use one row at a time and find the first occurrence of 1. return n-mid and compare.__

```C++
int fun(vector<int>& arr,int n){
        
        int low =0 ;
        int high = n-1;
        
        while(low<=high){
            int mid = low+(high-low)/2;
            
            if(arr[mid]<1){
                low=mid+1;
            }else{
                if(mid == 0 || arr[mid] != arr[mid - 1]){
                    return n-mid;
                }else{
                    high=mid-1;
                }
            }
        }
        return 0;
    }
    int rowWithMax1s(vector<vector<int> > &arr) {
        // code here
        int m = arr.size();
        int curr_cnt=0;
        int ans=-1;
        for(int i=0;i<m;i++){
            int n = arr[i].size();
            int cnt = fun(arr[i],n);
            
            if(cnt>curr_cnt){
                curr_cnt=cnt;
                ans=i;
            }
        }
        return ans;
    }
```
