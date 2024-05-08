[Problem Link](https://www.geeksforgeeks.org/problems/root-to-leaf-paths/1)<br>
Given a Binary Tree of nodes, you need to find all the possible paths from the root node to all the leaf nodes of the binary tree.<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/ed75ff89-d338-47ce-a454-32d8358414e7)
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/5e8921c4-187a-45f0-b84b-1f4c2ed351af)

Your Task:
Your task is to complete the function Paths() which takes the root node as an argument and returns all the possible paths. (All the paths are printed in new lines by the driver's code.)<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(height of the tree)<br>

Constraints:
1<=n<=10^4<br>

__Intuition -> Use recursion. Traverse left subtree and when a leaf node is encountered , store the path in the ans , return and then traverse the right subtree.__

```C++
void fun(Node* root , vector<vector<int>>&ans , vector<int>temp){
      if(root==NULL){
          return;
      }
      
      if(root->left==NULL && root->right==NULL){
          temp.push_back(root->data);
          ans.push_back(temp);
          return;
      }
      
      temp.push_back(root->data);
      fun(root->left,ans,temp);
      fun(root->right,ans,temp);
      return;
  }
    vector<vector<int>> Paths(Node* root) {
        // code here
        vector<vector<int>>ans;
        vector<int>temp;
        fun(root,ans,temp);
        return ans;
    }
```
