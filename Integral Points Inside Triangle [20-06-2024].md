[Problem Link](https://www.geeksforgeeks.org/problems/integral-points-in-triangle5026/1)<br>

Given three non-collinear points whose co-ordinates are p(p1, p2), q(q1, q2) and r(r1, r2) in the X-Y plane. Return the number of integral / lattice points strictly inside the triangle formed by these points.
Note: - A point in the X-Y plane is said to be an integral / lattice point if both its coordinates are integral.<br>

Examples<br>

Input: p = (0,0), q = (0,5), r = (5,0)<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/34a46cba-4168-493c-a440-7e9c90e28cab)<br>

Output: 6<br>
Explanation: <br>

As shown in figure, points (1,1) (1,2) (1,3) (2,1) (2,2) and (3,1) are the integral points inside the triangle. So total 6 are there.<br>
Input: p = (62,-3), q = (5,-45), r = (-19,-23)<br>
Output: 1129<br>
Explanation: There are 1129 integral points in the triangle formed by p, q and r.<br>
Expected Time Complexity: O(Log 10^9)<br>
Expected Auxillary Space: O(1)<br>

Constraints:<br>
-10^9 ≤ x-coordinate, y-coordinate ≤ 10^9<br>

__Intuition ->Use Pick's theorem to find the number of integral points.__

```C++
long long int InternalCount(long long int p[], long long int q[], long long int r[]) {
        
        // Pick's Theorem
        // A = i + B/2 - 1
        // i = A - B/2 + 1
        
        // A = area of the polygon (triangle in this case)
        // i = integral points inside polygon
        // B = integral points on boundary
        
        // Calculate the area of the triangle using the determinant method
        long long int area = (abs(p[0] * (q[1] - r[1]) + q[0] * (r[1] - p[1]) + r[0] * (p[1] - q[1])))/2;
        
        // Calculate the number of boundary points using the gcd of the differences
        long long int b1 = __gcd(abs(p[0] - q[0]), abs(p[1] - q[1]));
        long long int b2 = __gcd(abs(q[0] - r[0]), abs(q[1] - r[1]));
        long long int b3 = __gcd(abs(r[0] - p[0]), abs(r[1] - p[1]));
        
        // Total number of boundary points
        long long int boundaryPoints = b1 + b2 + b3;
        
        // Calculate the number of integral points inside the triangle using Pick's Theorem
        long long int integralPoints = area - boundaryPoints / 2 + 1;
        
        return integralPoints;
    }
```
