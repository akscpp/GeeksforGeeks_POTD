[Problem Link](https://www.geeksforgeeks.org/problems/magical-box5306/1)<br>

You are given a perimeter & the area. Your task is to return the maximum volume that can be made in the form of a cuboid from the given perimeter and surface area.<br>
Note: Round off to 2 decimal places and for the given parameters, it is guaranteed that an answer always exists.<br>

Examples<br>

Input: perimeter = 22, area = 15<br>
Output: 3.02<br>
Explanation: The maximum attainable volume of the cuboid is 3.02<br>
Input: perimeter = 20, area = 5<br>
Output: 0.33<br>
Explanation: The maximum attainable volume of the cuboid is 0.33<br>
Expected Time Complexity: O(1)<br>
Expected Auxiliary Space: O(1)<br>
Constraints :<br>
1 ≤ perimeter ≤ 10^9<br>
1 ≤ area ≤ 10^9<br>

__Intuition ->The solution finds the maximum cuboid volume given its perimeter and surface area by deriving its dimensions using algebraic manipulation. The width (l) is calculated using a quadratic equation based on the perimeter and area, and the height is then derived from the perimeter. The volume is computed with these dimensions, ensuring they satisfy both constraints, achieving the maximal volume efficiently in constant time, O(1).__

```C++
double maxVolume(double P, double A) {
        
        double l = (double)(P- sqrt(P*P-24*A))/12;
        
        double height = (P/4)-(2*(l));
        
        double ans = l*l*height;
        return ans;
    }
```
