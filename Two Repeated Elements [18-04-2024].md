[Problem Link](https://www.geeksforgeeks.org/problems/two-repeated-elements-1587115621/1)<br>
You are given an integer n and an integer array arr of size n+2. All elements of the array are in the range from 1 to n. Also, all elements occur once except two numbers which occur twice. Find the two repeating numbers.<br>
Note: Return the numbers in their order of appearing twice. So, if X and Y are the repeating numbers, and X's second appearance comes before second appearance of Y, then the order should be (X, Y).<br>

Example 1:<br>

Input:
n = 4<br>
arr[] = {1,2,1,3,4,3}<br>
Output: 
1 3<br>
Explanation: <br>
In the given array, 1 and 3 are repeated two times and as 1's second appearance occurs before 2's second appearance, so the output should be 1 3.<br>
Example 2:<br>

Input:
n = 2<br>
arr[] = {1,2,2,1}<br>
Output: 
2 1<br>
Explanation: <br>
In the given array, 1 and 2 are repeated two times and second occurence of 2 comes before 1. So the output is 2 1.<br>
Your Task:<br>
The task is to complete the function repeatedElements() which takes an integer array arr[] and an integer n as inputs (the size of the array is n + 2 and elements are in the range [1, n]) and finds the two repeated elements in the array and return them in an array.<br>

Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(1). <br>

Constraints:<br>
2 ≤ n ≤ 10^5<br>
1 ≤ arr[i] ≤ n<br>

__Intuition -> Traverse through the array and treat elements as index . If the arr[arr[i]] is +ve , make it negative and move to next index. If arr[arr[i]] is -ve , arr[i] is the repeating element since it sent us to an index which is previously visited.__

```C++
vector<int> twoRepeated (int arr[], int n) {
        // Your code here
        vector<int>ans;
        
        for(int i=0;i<n+2;i++){
            int idx = abs(arr[i]);
            
            if(arr[idx]<0){
                ans.push_back(idx);
            }else{
                arr[idx]= (-1)*arr[idx];
            }
        }
        return ans;
    }
```
