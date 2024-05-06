[Problem Link](https://www.geeksforgeeks.org/problems/print-all-nodes-that-dont-have-sibling/1)<br>

Given a Binary Tree of n nodes, find all the nodes that don't have any siblings. You need to return a list of integers containing all the nodes that don't have a sibling in sorted order (Increasing).

Two nodes are said to be siblings if they are present at the same level, and their parents are the same.

Note: The root node can not have a sibling so it cannot be included in our answer.


![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/0b242c86-a282-4f7b-9bbb-6131b6c14d11)

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/075ca70e-68f7-43ec-bb42-7f16e1d0bff3)

__Intuition ->The noSibling function traverses a binary tree to identify and return the values of nodes that do not have siblings. Employing a recursive approach, the function initializes an empty vector to collect these values. During traversal, if a node is a leaf node or has only one child, its value is appended to the vector. After traversal, if no such nodes are found, the function returns a vector containing only -1. Otherwise, the vector is sorted in ascending order before being returned. This approach efficiently identifies nodes lacking siblings, providing valuable insight into the tree's structure.__

```C++
void sib(Node* node , vector<int>&ans)
{
    if(node==nullptr) return;
    if((node->left==nullptr) ^ (node->right == nullptr))
    {
        if(node->left)ans.push_back(node->left->data);
        else ans.push_back(node->right->data);
    }
    sib(node->left,ans);
    sib(node->right,ans);
}
vector<int> noSibling(Node* node)
{
    // code here
    vector<int> ans;
    sib(node,ans);
    if(ans.size()==0) return {-1};
    sort(ans.begin(),ans.end());
    return ans;
}
```



