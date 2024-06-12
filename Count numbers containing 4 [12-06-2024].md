[Problem Link](https://www.geeksforgeeks.org/problems/count-numbers-containing-43022/1)<br>

You are given a number n, Return the count of total numbers from 1 to n containing 4 as a digit.<br>

Examples:<br>

Input: n = 9<br>
Output: 1<br>
Explanation: 4 is the only number between 1 to 9 which contains 4 as a digit.<br>
Input: n = 44<br>
Output: 9<br>
Explanation: 4, 14, 24, 34, 40, 41, 42, 43 & 44, there are total 9 numbers containing 4 as a digit.<br>
Expected Time Complexity: O(nlogn)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 <= n <= 10^5<br>

__Intuition ->Traverse from 4 to n . For each i , check its digits.__

```C++
int countNumberswith4(int n) {
        // code here
        int ans = 0;
        
        for(int i=4;i<=n;i++){
            
            int j = i;
            
            while(j!=0){
                if(j%10==4){
                    ans++;
                    break;
                }
                j = j/10;
            }
        }
        
        return ans;
    }
```
