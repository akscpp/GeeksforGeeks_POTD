[Problem Link](https://www.geeksforgeeks.org/problems/maximum-tip-calculator2631/1)<br>

In a restaurant, two waiters, A and B, receive n orders per day, earning tips as per arrays arr[i] and brr[i] respectively. If A takes the ith order, the tip is arr[i] rupees; if B takes it, the tip is brr[i] rupees.<br>

To maximize total tips, they must distribute the orders such that:<br>

A can handle at most x orders<br>
B can handle at most y orders<br>
Given that x + y ≥ n, all orders can be managed by either A or B. Return the maximum possible total tip after processing all the orders.<br>

Examples<br>

Input: n = 5, x = 3, y = 3, arr = {1, 2, 3, 4, 5}, brr = {5, 4, 3, 2, 1}<br>
Output: 21<br>
Explanation: Person A will serve the 3rd, 4th and 5th order while person B will serve the rest so the total tip from A = 3+4+5 & B = 5 + 4 i.e. 21. <br>
 

Input: n = 8, x = 4, y = 4, arr = {1, 4, 3, 2, 7, 5, 9, 6}, brr = {1, 2, 3, 6, 5, 4, 9, 8}<br>
Output: 43<br>
Explanation: Person A will serve 1st, 2nd, 5th and 6th order while Person B will serve the rest & the total tip will be 43.<br>
 

Input: n = 7, x = 3, y = 4, arr[] = {8, 7, 15, 19, 16, 16, 18}, brr[] = {1, 7, 15, 11, 12, 31, 9}<br>
Output: 110<br>
Explanation: Person A will serve orders 8,19,18 while person B will serve 7,15, 12 & 31.<br>
Expected Time Complexity: O(n*logn)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 ≤ n ≤ 10^5<br>
1 ≤ x, y ≤ n<br>
1 ≤ arr[i], brr[i] ≤ 10^9<br>

__Intuition ->Use a temp array to store pair of absolute difference between tips and its corresponding index. Now , sort it and traverse till n tips are not collected by comparing tips at index.__

```C++
long long maxTip(int n, int x, int y, vector<int> &arr, vector<int> &brr) {
        // code here
        
        vector<pair<int,int>>temp;
        
        for(int i=0;i<n;i++){
            temp.push_back({abs(arr[i]-brr[i]),i});
        }
        
        long long ans = 0;
        
        sort(temp.begin(),temp.end());
        
        for(int i=n-1;i>=0;i--){
            int idx = temp[i].second;
            
            if(arr[idx]>brr[idx]){
                
                if(x){
                    ans+= arr[idx];
                    x--;
                }else{
                    ans+= brr[idx];
                    y--;
                }
            }else{
                
                if(y){
                    ans+= brr[idx];
                    y--;
                }else{
                    ans+= arr[idx];
                    x--;
                }
            }
        }
        
        return ans;
    }
```

