[Problem Link](https://www.geeksforgeeks.org/problems/k-distance-from-root/1)<br>

Given a binary tree having n nodes and an integer k. Print all nodes that are at distance k from the root (root is considered at distance 0 from itself). Nodes should be printed from left to right.<br>

Example 1:<br>

Input:<br>
k = 0<br>
      1<br>
    /   \ <br>
   3     2<br>
Output: 
1<br>
Explanation: 
1 is the only node which is 0 distance from the root 1.<br>
Example 2:<br>

Input:<br>
k = 3<br>
        1<br>
       / <br>
      2<br>
       \ <br>
        1<br>
      /  \ <br>
     5    3<br>
Output: 
5 3<br>
Explanation:  
5 and 3 are the nodes which are at distance 3 from the root 3.<br>
Here, returning 3 5 will be incorrect.<br>
Your Task:
You don't have to take input. Complete the function Kdistance() that accepts root node and k as parameters and returns the value of the nodes that are at a distance k from the root.<br>

Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(Height of the Tree).<br>

Constraints:<br>
1 <= n <= 10^4<br>
0 <= k <= 30<br>

__Intuition -> Use recursion. At every call for left and right subtree , reduce the value of k by 1. When k becomes 0 , include that nodes value in  the answer vector and return.__

```C++
void fun(struct Node* root , int k , vector<int>&ans){
        if(root==NULL) return;
        
        if(k==0){
            ans.push_back(root->data);
            return;
        }
        
        fun(root->left,k-1,ans);
        fun(root->right,k-1,ans);
        return;
    }
    vector<int> Kdistance(struct Node *root, int k)
    {
      // Your code here
      vector<int>ans;
      
      fun(root,k,ans);
      
      return ans;
    }
```
