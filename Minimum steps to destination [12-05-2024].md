[Problem Link](https://www.geeksforgeeks.org/problems/minimum-number-of-steps-to-reach-a-given-number5234/1)<br>
Given an infinite number line. You start at 0 and can go either to the left or to the right. The condition is that in the ith move, you must take i steps. Given a destination d, find the minimum number of steps required to reach that destination.<br>

Example 1:<br>

Input: d = 2<br>
Output: 3<br>
Explaination: The steps takn are +1, -2 and +3.<br>
Example 2:<br>

Input: d = 10<br>
Output: 4<br>
Explaination: The steps are +1, +2, +3 and +4.<br>
Your Task:
You do not need to read input or print anything. Your task is to complete the function minSteps() which takes the value d as input parameter and returns the minimum number of steps required to reach the destination d from 0.<br>

Expected Time Complexity: O(d)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
1 ≤ d ≤ 10000<br>

__Intuition ->This code iteratively finds the minimum steps to reach a destination on an infinite number line. It keeps increasing the step size and traveled distance until it can land on the destination in an even number of steps, avoiding overshooting.__

```C++
int minSteps(int d) {
        // code here
        int sum=0;
        int steps=0;
        
        while(sum<d ||(sum-d)%2!=0){
            steps++;
            
            sum+=steps;
        }
        
        return steps;
    }
```
