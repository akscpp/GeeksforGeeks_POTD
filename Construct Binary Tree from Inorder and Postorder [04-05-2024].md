[Problem Link](https://www.geeksforgeeks.org/problems/tree-from-postorder-and-inorder/1)<br>
Given inorder and postorder traversals of a binary tree(having n nodes) in the arrays in[] and post[] respectively. The task is to construct a binary tree from these traversals.<br>

Driver code will print the preorder traversal of the constructed tree.<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/aa77832d-71c1-4c97-b327-b5f2f9001b93)<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/23c5c3fc-8393-4dad-82d2-2563cdaa29f1)<br>


Your Task:<br>
You do not need to read input or print anything. Complete the function buildTree() which takes the inorder, postorder traversals and the number of nodes in the tree as input parameters and returns the root node of the newly constructed Binary Tree.<br>

Expected Time Complexity: O(n^2)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 <= n <= 10^3<br>
1 <= in[i], post[i] <= 10^6<br>

__Intuition -> Use 4 pointers to play with index. The last element of postorder always gives root. Now , search this root (value) in inorder, all the element before this is in left subtree and all the elements right of the root(value) are in right subtree.__

```C++
Node* fun(int in[],int pos[], int inStart , int inEnd , int posStart, int posEnd){
        if(inStart>inEnd) return NULL;
        
        if(inStart==inEnd) {
            return new Node(in[inStart]);
        }
        
        Node* root = new Node(pos[posEnd]);
        int ind=-1;
        
        for(int i=inStart;i<=inEnd;i++){
            if(in[i]==pos[posEnd]){
                ind=i;
                break;
            }
        }
        
        int left = ind - inStart;
        int right = inEnd-ind;
        
        root->left = fun(in,pos,inStart,ind-1,posStart,posStart+left-1);
        
        root->right = fun(in,pos,ind+1,inEnd,posEnd-right,posEnd-1);
        
        return root;
        
    }
    Node *buildTree(int in[], int post[], int n) {
        // Your code here
        return fun(in,post,0,n-1,0,n-1);
    }
```
