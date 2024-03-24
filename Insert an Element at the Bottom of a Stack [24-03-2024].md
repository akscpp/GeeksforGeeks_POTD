[Problem Link](https://www.geeksforgeeks.org/problems/insert-an-element-at-the-bottom-of-a-stack/1)<br>

You are given a stack st of n integers and an element x. You have to insert x at the bottom of the given stack. <br>

Note: Everywhere in this problem, the bottommost element of the stack is shown first while priniting the stack.<br>

Example 1:<br>

Input:<br>
n = 5<br>
x = 2<br>
st = {4,3,2,1,8}<br>
Output:<br>
{2,4,3,2,1,8}<br>
Explanation:<br>
After insertion of 2, the final stack will be {2,4,3,2,1,8}.<br>
Example 2:<br>

Input:<br>
n = 3<br>
x = 4<br>
st = {5,3,1}<br>
Output:<br>
{4,5,3,1}<br>
Explanation:<br>
After insertion of 4, the final stack will be {4,5,3,1}.<br>
Your Task:<br>

You don't need to read input or print anything. Your task is to complete the function insertAtBottom() which takes a stack st and an integer x as inputs and returns the modified stack after insertion.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 <= n <= 10^5<br>
0 <= x, elements of stack <= 10^9<br>

__Intuition -> Use another stack to store elements . Insert the element and fill the stack once again.__

```C++
    stack<int> insertAtBottom(stack<int> st,int x){
        stack<int>temp;
        while(st.size()>=1){
            temp.push(st.top());
            st.pop();
        }
        st.push(x);
        while(!temp.empty()){
            st.push(temp.top());
            temp.pop();
        }
        return st;
    }
```
