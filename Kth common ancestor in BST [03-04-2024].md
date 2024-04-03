[Problem Link](https://www.geeksforgeeks.org/problems/kth-common-ancestor-in-bst/1)<br>
Given a BST with n (n>=2) nodes, find the kth common ancestor of nodes x and y in the given tree. Return -1 if kth ancestor does not exist.<br>

Nodes x and y will always be present in the input of a BST, and x != y.<br>

Example 1:<br>

Input: <br>
Input tree<br>

k = 2, x = 40, y = 60 <br>
Output:
30<br>
Explanation:
Their 2nd common ancestor is 30.<br>
Example 2:<br>

Input: <br>
Input tree<br>

k = 2, x = 40, y = 60<br>
Output:
-1<br>
Explanation:
LCA of 40 and 60 is 50, which is root itself. There does not exists 2nd common ancestor in this case.<br>
Your task :
You don't have to read input or print anything. Your task is to complete the function kthCommonAncestor() that takes the root of the tree, k, x and y as input and returns the kth common ancestor of x and y.<br>
 
Expected Time Complexity: O(Height of the Tree)<br>
Expected Space Complexity: O(Height of the Tree)<br>
 
Your Task :
1 <= n, k <= 10^5<br>
1 <= node->data, x, y <= 10^9<br>

__Intuition -> Find LCA . Then ,  store the path from root to the LCA to keep track of the ancestors. (All nodes from root to LCA will be the ancestors). If LCA is not present , return -1 . If kth ancestor is not present (k > number of nodes in the path from root to LCA) ,  return -1. Else return n-k th node's value.__

```C++
Node* LCA(Node* root , int x , int y){
        if(root==NULL) return NULL;
        if(root->data==x || root->data==y) return root;
        
        Node* lcaL = LCA(root->left,x,y);
        Node* lcaR = LCA(root->right,x,y);
        
        if(lcaL !=NULL && lcaR!=NULL){
            return root;
        }
        
        if(lcaL!=NULL) return lcaL;
        else return lcaR;
    }
    void pathFromRoot(Node* root,Node* Lca,vector<int>&temp){
        temp.push_back(root->data);
        if(root->data<Lca->data){
            pathFromRoot(root->right,Lca,temp);
        }
        else if(root->data>Lca->data){
            pathFromRoot(root->left,Lca,temp);
        }
        else return;
        
        
    }
    
    /*You are required to complete below function */
    int kthCommonAncestor(Node *root, int k,int x, int y)
    {
        // your code goes here
        Node* lca = LCA(root,x,y);
        vector<int>temp;
        if(lca==NULL) return -1;
        pathFromRoot(root,lca,temp);
        
        int nodes = temp.size();
        
        if(k>nodes) return -1;
        
        return temp[nodes-k];
        
    }
```
