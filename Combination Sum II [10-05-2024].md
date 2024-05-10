[Problem Link](https://www.geeksforgeeks.org/problems/combination-sum-ii-1664263832/1)<br>
Given an array of integers arr, the length of the array n, and an integer k, find all the unique combinations in arr where the sum of the combination is equal to k. Each number can only be used once in a combination.<br>
Return the combinations in the lexicographically sorted order, where each combination is in non-decreasing order.<br>

Example 1:<br>

Input: 
n = 5, k = 7<br>
arr[] = { 1, 2, 3, 3, 5 }<br>
Output:<br>
{ { 1, 3, 3 }, { 2, 5 } }<br>
Explanation:
1 + 3 + 3 = 7<br>
2 + 5 = 7<br>
Example 2:<br>

Input:
n = 6, k = 30<br>
arr[] = { 5, 10, 15, 20, 25, 30 }<br>
Output:
{ { 5, 10, 15 }, { 5, 25 }, { 10, 20 }, { 30 } }<br>
Explanation:
5 + 10 + 15 = 30<br>
5 + 25 = 30<br>
10 + 20 = 30<br>
Your Task:
You don't need to read input or print anything. Your task is to complete the function CombinationSum2() which takes arr[],n, and k as input parameters and returns all the unique combinations.<br>
 

Constraints:
1 <= n <= 100<br>
1 <= arr[i] <= 50<br>
1 <= k <= 30<br>

let p = number of elements, at maximum, can sum up to the given value k.<br>

Expected Time Complexity: O(2^min(n,p))<br>
Expected Auxiliary Space: O(n)<br>

__Intuition ->Use concept of take and don't take.At the same time , increase the sum when taking an element. If the sum becomes equal to k , store the elements in answer.__

```C++
void fun(int ind , int sum,int k , int n , vector<int>&arr,vector<int>&temp,set<vector<int>>&st){
        if(sum==k){
            st.insert(temp);
            return;
        }
        
        if(ind==n) return;
        
        fun(ind+1,sum,k,n,arr,temp,st);
        
        if(arr[ind]+sum<=k){
            temp.push_back(arr[ind]);
            fun(ind+1,sum+arr[ind],k,n,arr,temp,st);
            temp.pop_back();
        }
    }
    
    
    vector<vector<int>> CombinationSum2(vector<int> arr,int n,int k)
    {
        //code here
        sort(arr.begin(),arr.end());
        vector<int>temp;
        set<vector<int>>st;
        fun(0,0,k,n,arr,temp,st);
        
        vector<vector<int>>res(st.begin(),st.end());
        return res;
    }
```
