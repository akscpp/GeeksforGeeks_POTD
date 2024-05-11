[Problem Link](https://www.geeksforgeeks.org/problems/juggler-sequence3930/1)<br>
Juggler Sequence is a series of integers in which the first term starts with a positive integer number a and the remaining terms are generated from the immediate previous term using the below recurrence relation:<br>

Juggler Formula<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/a4926404-494c-456c-92ca-45917238d36e)


Given a number n, find the Juggler Sequence for this number as the first term of the sequence until it becomes 1.<br>


Example 1:<br>

Input: n = 9<br>
Output: 9 27 140 11 36 6 2 1<br>
Explaination: We start with 9 and use 
above formula to get next terms.<br>
 

Example 2:<br>

Input: n = 6<br>
Output: 6 2 1<br>
Explaination: <br>
[6^(1/2)] = 2. <br>
[2^(1/2)] = 1.<br>
 

Your Task:
You do not need to read input or print anything. Your Task is to complete the function jugglerSequence() which takes n as the input parameter and returns a list of integers denoting the generated sequence.<br>

 

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

 

Constraints:
1 ≤ n ≤ 100<br>

__Intuition -> Simulate the question.__

```C++
vector<long long> jugglerSequence(long long n) {
        // code here
        vector<long long>ans;
       while (n != 1) {
        ans.push_back(n);
        if (n % 2 == 0) {
            n = std::pow(n, 1.0/2.0); 
        } else {
            n = std::pow(n, 3.0/2.0); 
        }
    }
    ans.push_back(1); 
    return ans;
    }
```
