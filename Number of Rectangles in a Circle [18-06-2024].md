[Problem Link](https://www.geeksforgeeks.org/problems/rectangles-in-a-circle0457/1)<br>

Given a circular sheet of radius, r. Find the total number of rectangles with integral length and width that can be cut from the sheet that can fit on the circle, one at a time.<br>

Examples :<br>

Input: r=1<br>
Output: 1<br>
Explanation: Only 1 rectangle of dimensions 1x1.<br>
Input: r=2<br>
Output: 8<br>
Explanation: The 8 possible rectangles are <br>
(1x1)(1x2)(1x3)(2x1)(2x2)(2x3)(3x1)(3x2).<br>
Expected Time Complexity: O(r^2)<br>
Expected Auxillary Space: O(1)<br>


Constraints:
1<=r<=1000 <br>

__Intuition ->Since the maximum diagonal length of a rectangle can be of length 4r, we will just count the number of rectangles with diagonal length <=4r.__

```C++
int rectanglesInCircle(int r) {
        // code here
        
        int cnt = 0;
        
        for(int i=1;i<(2*r);i++){
            for(int j=1;j<(2*r);j++){
                if(i*i + j*j <= 4*r*r){
                    cnt++;
                }
            }
        }
        return cnt;
    }
```
