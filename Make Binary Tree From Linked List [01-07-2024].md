[Problem Link](https://www.geeksforgeeks.org/problems/make-binary-tree/1)<br>

Given a Linked List Representation of Complete Binary Tree. The task is to construct the Binary tree and print the level order traversal of the Binary tree. 
Note: The complete binary tree is represented as a linked list in a way where if the root node is stored at position i, its left, and right children are stored at position 2*i+1, and 2*i+2 respectively. H is the height of the tree and this space is used implicitly for the recursion stack.<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/0d501529-696d-4464-b4b0-183e155cf95e)
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/7677516c-32f1-4c77-a055-7b508253dad2)
<br>
Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(n).<br>
Constraints:<br>
1 <= n <= 10^5<br>
1 <= ki <= 10^5<br>

__Intuition->Traverse the linkedList and store all the values in a vector. Now, use recursion to construct the binary tree.__

```C++
TreeNode* construct(int idx,vector<int>& ans,int n){
    if(idx>=n){
        return NULL;
    }
    TreeNode* roots = new TreeNode(ans[idx]);
    roots->left = construct((2*idx)+1,ans,n);
    roots->right = construct((2*idx)+2,ans,n);
    return roots;
    
}
void convert(Node *head, TreeNode *&root) {
    // Your code here
    vector<int>nodes;
    Node* p = head;
    while(p){
        nodes.push_back(p->data);
        p=p->next;
    }
    int n = nodes.size();
    
    root=construct(0,nodes,n);
    
}
```
