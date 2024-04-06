[Problem Link](https://www.geeksforgeeks.org/problems/count-ways-to-nth-stairorder-does-not-matter1322/1)<br>
There are n stairs, and a person standing at the bottom wants to reach the top. The person can climb either 1 stair or 2 stairs at a time. Count the number of ways, the person can reach the top (order does not matter).<br>

Example 1:<br>

Input:
n = 4<br>
Output: 
3<br>
Explanation: 
You can reach 4th stair in 3 ways.
3 possible ways are:<br>
1, 1, 1, 1<br>
1, 1, 2<br>
2, 2<br>
Here, note that {1, 1, 2}, {1, 2, 1} and {2, 1, 1} are considered same as their order does not matter. <br>
Example 2:<br>

Input:
n = 5<br>
Output: 
3<br>
Explanation:
You may reach the 5th stair in 3 ways.
The 3 possible ways are:<br>
1, 1, 1, 1, 1<br>
1, 1, 1, 2<br>
1, 2, 2<br>
Your Task:
Your task is to complete the function countWays() which takes a single argument n and returns the answer.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>
Constraints:<br>
1 <= N <= 10^6<br>

__Intuition ->Since the order does not matter , we can say that the number of ways will be n/2 + 1.__

```C++
long long countWays(int n) {
        // your code here
        return (n/2)+1;
    }
```
