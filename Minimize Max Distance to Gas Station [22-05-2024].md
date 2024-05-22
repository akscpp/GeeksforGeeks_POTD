[Problem Link](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1)<br>
We have a horizontal number line. On that number line, we have gas stations at positions stations[0], stations[1], ..., stations[N-1], where n = size of the stations array. Now, we add k more gas stations so that d, the maximum distance between adjacent gas stations, is minimized. We have to find the smallest possible value of d. Find the answer exactly to 2 decimal places.<br>

Example 1:<br>

Input:
n = 10<br>
stations = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]<br>
k = 9<br>
Output: 0.50<br>
Explanation: Each of the 9 stations can be added mid way between all the existing adjacent stations.<br>
Example 2:<br>

Input:
n = 10<br>
stations = [3,6,12,19,33,44,67,72,89,95] <br>
k = 2 <br>
Output: 14.00 <br>
Explanation: Construction of gas stations at 8th(between 72 and 89) and 6th(between 44 and 67) locations.<br>
 

Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function findSmallestMaxDist() which takes a list of stations and integer k as inputs and returns the smallest possible value of d. Find the answer exactly to 2 decimal places.<br>

Expected Time Complexity: O(n*log k)<br>
Expected Auxiliary Space: O(1)<br>

__Intuition -> Do binary search on the possible distance. Check if a picked distance is possible or not. If it is possible , store it in answer and move with a lower distance.__

```C++
bool isPossible(vector<int>& s, double mid, int k) {
        int cnt = 0;
        int n = s.size();
        for (int i = 1; i < n; ++i) {
            cnt += ceil((s[i] - s[i - 1]) / mid) - 1;
        }
        return cnt <= k;
    }
    double findSmallestMaxDist(vector<int> & s, int k) {
        // Code here
        double st = 0.0;
        double en = s.back() - s.front(); 
        double ans = en;
        while (en - st > 1e-6) {
            double mid = st + (en - st) / 2.0;
            if (isPossible(s, mid, k)) {
                ans = mid;
                en = mid;
            } else {
                st = mid;
            }
        }
        return ans;
    }
```

Constraint:
10 <= n <= 5000 
0 <= stations[i] <= 109 
0 <= k <= 105

stations is sorted in a strictly increasing order.
