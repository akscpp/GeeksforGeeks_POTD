[Problem Link](https://www.geeksforgeeks.org/problems/construct-list-using-given-q-xor-queries/1)<br>

Given a list s that initially contains only a single value 0. There will be q queries of the following types:<br>

0 x: Insert x in the list<br>
1 x: For every element a in s, replace it with a ^ x. ('^' denotes the bitwise XOR operator)<br>
Return the sorted list after performing the given q queries.<br>

Example 1:<br>

Input:
q = 5<br>
queries[] = {{0, 6}, {0, 3}, {0, 2}, {1, 4}, {1, 5}}<br>
Output:
1 2 3 7<br>
Explanation:<br>
[0] (initial value)<br>
[0 6] (add 6 to list)<br>
[0 6 3] (add 3 to list)<br>
[0 6 3 2] (add 2 to list)<br>
[4 2 7 6] (XOR each element by 4)<br>
[1 7 2 3] (XOR each element by 5)<br>
The sorted list after performing all the queries is [1 2 3 7]. <br>
Example 2:<br>
Input:
q = 3<br>
queries[] = {{0, 2}, {1, 3}, {0, 5}} <br>
Output :
1 3 5<br>
Explanation:<br>
[0] (initial value)<br>
[0 2] (add 2 to list)<br>
[3 1] (XOR each element by 3)<br>
[3 1 5] (add 5 to list)<br>
The sorted list after performing all the queries is [1 3 5].<br>

Your Task:  
You don't need to read input or print anything. Your task is to complete the function constructList() which takes an integer q the number of queries and queries[] a list of lists of length 2 denoting the queries as input parameters and returns the final constructed list.<br>


Expected Time Complexity: O(q*log(q))<br>
Expected Auxiliary Space: O(l), where l is only used for output-specific requirements.<br>


Constraints:<br>
1 ≤ q ≤ 10^5<br>

__Intuition ->Start from right side and keep track of current xor. Whenever 1 is encountered , change the xor and apply this to 0 while moving left.__

```C++
vector<int> constructList(int q, vector<vector<int>> &queries) {
        // code here
        vector<int>v;
        
        int last_xor=0;
        for(int i=q-1;i>=0;i--){
            if(queries[i][0]==1){
                last_xor^=queries[i][1];
            }else{
                v.push_back(queries[i][1]^last_xor);
            }
        }
        v.push_back(last_xor);
        sort(v.begin(),v.end());
        
        return v;
    }
```
