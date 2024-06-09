[Problem Link](https://www.geeksforgeeks.org/problems/convert-array-into-zig-zag-fashion1638/1)<br>

Given an array arr of distinct elements of size n, the task is to rearrange the elements of the array in a zig-zag fashion so that the converted array should be in the below form: <br>

arr[0] < arr[1]  > arr[2] < arr[3] > arr[4] < . . . . arr[n-2] < arr[n-1] > arr[n]. <br>

Note: Modify the given arr[] only, If your transformation is correct, the output will be 1 else the output will be 0. <br>

Examples<br>

Input: n = 7, arr[] = {4, 3, 7, 8, 6, 2, 1}<br>
Output: 1<br>
Explanation:  After modification the array will look like 3 < 7 > 4 < 8 > 2 < 6 > 1, the checker in the driver code will produce 1.<br>
Input: n = 5, arr[] = {4, 7, 3, 8, 2}<br>
Output: 1<br>
Explanation: After modification the array will look like 4 < 7 > 3 < 8 > 2 hence output will be 1.<br>
Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 <= n <= 10^6<br>
0 <= arr[i] <= 10^9<br>

__Intuition ->Use a flag to keep track of < or >. If the current element violates the condition , swap it .__

```C++
void zigZag(int n, vector<int> &arr) {
        // code here
        bool flag = 0;
        
        //flag -> 0  (we need <)
        //flag -> 1  (we need >)
        for(int i=0;i<n-1;i++){
            
            if(flag==0){
                
                //Check for violation
                if(arr[i]>arr[i+1]){
                    swap(arr[i],arr[i+1]);
                }
            }else{
                
                //Check for violation
                if(arr[i]<arr[i+1]){
                    swap(arr[i],arr[i+1]);
                }
            }
            
            flag = !flag;
        }
    }
```
