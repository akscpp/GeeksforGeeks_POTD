[Problem Link](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)<br>

You are given timings of n meetings in the form of (start[i], end[i]) where start[i] is the start time of meeting i and end[i] is the finish time of meeting i. Return the maximum number of meetings that can be accommodated in a single meeting room, when only one meeting can be held in the meeting room at a particular time. <br>

Note: The start time of one chosen meeting can't be equal to the end time of the other chosen meeting.<br>

Examples :<br>

Input: n = 6, start[] = [1, 3, 0, 5, 8, 5], end[] =  [2, 4, 6, 7, 9, 9]<br>
Output: 4<br>
Explanation: Maximum four meetings can be held with given start and end timings. The meetings are - (1, 2), (3, 4), (5,7) and (8,9)<br>
Input: n = 3, start[] = [10, 12, 20], end[] = [20, 25, 30]<br>
Output: 1<br>
Explanation: Only one meetings can be held with given start and end timings.<br>
Expected Time Complexity: O(n*logn)<br>
Expected Auxilliary Space: O(n)<br>

Constraints:<br>
1 ≤ n ≤ 10^5<br>
0 ≤ start[i] < end[i] ≤ 10^6<br>

__Intuition ->Make a vector of pair containing start time and end time. Sort it in ascending order according to the end time. Now, cnt the intervals with starting time > end time of previous taken interval.__

```C++
static bool myCmp(pair<int,int>a , pair<int,int>b){
        return a.second<b.second;
    }
    int maxMeetings(int n, int start[], int end[]) {
        vector<pair<int,int>>vec(n);
        
        for(int i=0;i<n;i++){
            vec[i]={start[i],end[i]};
        }
        
        sort(vec.begin(),vec.end(),myCmp);
        int cnt=1;
        int ind=0;
        
        for(int i=1;i<n;i++){
            if(vec[i].first>vec[ind].first && vec[i].first>vec[ind].second){
                cnt++;
                ind = i;
            }
        }
        
        return cnt;
    }
```
