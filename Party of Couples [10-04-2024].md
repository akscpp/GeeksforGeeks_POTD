[Problem Link](https://www.geeksforgeeks.org/problems/alone-in-couple5507/1)<br>
You are given an integer array arr[] of size n, representing n number of people in a party, each person is denoted by an integer. Couples are represented by the same number ie: two people have the same integer value, it means they are a couple. Find out the only single person in the party of couples.<br>

NOTE: It is guarantee that there exist only one single person in the party.<br>

Example 1:<br>

Input: 
n = 5<br>
arr = {1, 2, 3, 2, 1}<br>
Output: 
3<br>
Explaination: Only the number 3 is single.<br>
Example 2:<br>

Input: 
n = 11 <br>
arr = {1, 2, 3, 5, 3, 2, 1, 4, 5, 6, 6} <br>
Output: 
4 <br>
Explaination: 4 is the only single.<br>
Your Task:<br>
You do not need to read input or print anything. Your task is to complete the function findSingle() which takes the size of the array n and the array arr[] as input parameters and returns the only single person.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 ≤ n ≤ 10^4<br>
1 ≤ arr[i] ≤ 10^6<br>


__Intuition->We need to find single appearing element . Since we know that X^X = 0 and X^0 = X , we can use XOR. Take XOR of all the array elements.__
```C++
int findSingle(int n, int arr[]){
        int XOR=0;
        for(int i=0;i<n;i++){
            XOR^=arr[i];
        }
        return XOR;
    }
```
