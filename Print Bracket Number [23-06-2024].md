[Problem Link](https://www.geeksforgeeks.org/problems/print-bracket-number4058/1)<br>
Given a string str, the task is to find the bracket numbers, i.e., for each bracket in str, return i if the bracket is the ith opening or closing bracket to appear in the string.<br>

 Examples:<br>

Input:  str = "(aa(bdc))p(dee)"<br>
Output: 1 2 2 1 3 3<br>
Explanation: The highlighted brackets in
the given string (aa(bdc))p(dee) are
assigned the numbers as: 1 2 2 1 3 3.<br>
Input:  str = "(((()("<br>
Output: 1 2 3 4 4 5<br>
Explanation: The highlighted brackets in
the given string (((()( are assigned
the numbers as: 1 2 3 4 4 5<br>
Expected Time Complexity: O(|str|)<br>
Expected Auxiliary Space: O(|str|)<br>

Constraints:<br>
1 <= |str| <= 10^5<br>
str contains lowercase English alphabets, and '(', ')' characters<br>
At any index, the number of opening brackets is greater than or equal to closing brackets<br>

__Intuition ->Use stack to store the bracket number and pop it accordingy.__

```C++
vector<int> bracketNumbers(string str) {
        // Your code goes here
        int maxi = 1;
        
        stack<int>st;
        
        int n = str.length();
        vector<int>ans;
        
        for(int i=0;i<n;i++){
            if(str[i]=='(' || str[i]==')'){
                if(str[i]=='('){
                    st.push(maxi);
                    ans.push_back(maxi);
                    maxi++;
                }else{
                    ans.push_back(st.top());
                    st.pop();
                }
            }
        }
        return ans;
    }
```
