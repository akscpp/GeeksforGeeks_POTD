[Problem Link](https://www.geeksforgeeks.org/problems/reverse-level-order-traversal/1)<br>

Given a binary tree of size n, find its reverse level order traversal. ie- the traversal must begin from the last level.<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/1c2429a1-11ff-480d-9f31-0f38e2c8b033)
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/ae9a867c-cd1d-441f-b624-085d5af8ac40)


Your Task: 
You don't need to read input or print anything. Complete the function reverseLevelOrder() which takes the root of the tree as input parameter and returns a list containing the reverse level order traversal of the given tree.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:
1 ≤ n ≤ 10^4<br>

__Intuition -> Use level order traversal but store right child before left child. After queue becomes empty , reverse the vector.__

```C++
vector<int> reverseLevelOrder(Node *root)
{
    // code here
    vector<int>ans;
    
    queue<Node*>q;
    q.push(root);
    
    while(!q.empty()){
        Node* curr = q.front();
        
        q.pop();
        
        ans.push_back(curr->data);
        
        if(curr->right!=NULL) q.push(curr->right);
        if(curr->left!=NULL) q.push(curr->left);
    }
    
    reverse(ans.begin(),ans.end());
    return ans;
}
```
