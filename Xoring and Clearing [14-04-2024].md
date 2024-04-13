[Problem Link](https://www.geeksforgeeks.org/problems/xoring-and-clearing/1)<br>
You are given an array arr[] of size n. You need to do the following:<br>

You need to calculate the bitwise XOR of each element in the array with its corresponding index (indices start from 0).<br>
After step1, print the array.<br>
Now, set all the elements of arr[] to zero.<br>
Now, print arr[].<br>
Example 1:<br>

Input:
n = 10<br>
arr[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}<br>
Output:<br>
1 3 1 7 1 3 1 15 1 3<br>
0 0 0 0 0 0 0 0 0 0<br>
Explanation:<br>
First we take xor of every element with<br>
their indices, like (1xor0), (2xor1), (3xor2), (4xor3) and so on.<br>
Now print the resultant array<br>
Now set all the elements of array to zero<br>
Now print the resultant array<br>
Example 2:<br>

Input:
n = 4<br>
arr[] = {10, 20, 30, 40}<br>
Output:<br>
10 21 28 43<br>
0 0 0 0<br>
Explanation:<br>
First we take xor of every element with
their indices, like (1xor0), (2xor1), (3xor2).<br>
Now print the resultant array<br>
Now set all the elements of array to zero<br>
Now print the resultant array<br>
Your Task:
Since this is a function problem, you don't need to take any input. Just complete the provided functions. In a new line, print the output.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
1 <= n <= 1000<br>
1 <= arr[i] <= 1000<br>

__Intuition -> Do what the question says !.__

```C++
void printArr(int n, int arr[]) {
        
        for(int i=0;i<n;i++){
            cout<<arr[i]<<" ";
        }
        cout<<endl;
    }

    void setToZero(int n, int arr[]) {
        
        for(int i=0;i<n;i++) arr[i]=0;
        
    }

    void xor1ToN(int n, int arr[]) {
        
        for(int i=0;i<n;i++){
            arr[i]=arr[i]^i;
        }
        
    }
```
