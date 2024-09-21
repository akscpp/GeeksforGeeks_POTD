[Problem Link](https://www.geeksforgeeks.org/problems/ancestors-in-binary-tree/1)<br>
Given a Binary Tree and an integer target. Find all the ancestors of the given target.<br>

Note:<br>


The ancestor of node x is node y, which is at the upper level of node x, and x is directly connected with node y. Consider multiple levels of ancestors to solve this problem.<br>
In case there are no ancestors available, return an empty list.<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/6bc75172-279b-4d59-96d7-3cc97744aba4)<br>
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/6d688acb-265d-434a-a24d-470c2a8a92c4)<br>


Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(height of tree)<br>

Constraints:<br>
1 ≤ no. of nodes ≤ 10^3<br>
1 ≤ data of node ≤ 10^4<br>

__Intuition ->Keeping pushing the node data in the temp vector until you don't find the target node. When in a particular path , you don't encounter the target, pop the current node value and move to right subtree. When the target node is encountered, store the current path and return it.__<br>

```C++
void fun(Node* root, int target,vector<int>& ans,vector<int>&temp){
        if(root==NULL) return;
        if(root->data==target){
            ans=temp;
            return;
        }
        temp.push_back(root->data);
        fun(root->left,target,ans,temp);
        fun(root->right,target,ans,temp);
        temp.pop_back();
        
    }
    vector<int> Ancestors(struct Node *root, int target) {
        vector<int>ans;
        vector<int>temp;
        fun(root,target,ans,temp);
        reverse(ans.begin(),ans.end());
        return ans;
    }
```
