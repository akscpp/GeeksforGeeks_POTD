[Problem Link](https://www.geeksforgeeks.org/problems/serialize-and-deserialize-a-binary-tree/1)<br>
Serialization is to store a tree in an array so that it can be later restored and deserialization is reading tree back from the array. Complete the functions<br>

serialize() : stores the tree into an array a and returns the array.<br>
deSerialize() : deserializes the array to the tree and returns the root of the tree.<br>
Note: Multiple nodes can have the same data and the node values are always positive integers. Your code will be correct if the tree returned by deSerialize(serialize(input_tree)) is same as the input tree. Driver code will print the in-order traversal of the tree returned by deSerialize(serialize(input_tree)).<br>

Example 1:<br>

Input:<br>
      1<br>
    /   \<br>
   2     3<br>
Output: 
2 1 3<br>
Example 2:<br>

Input:<br>
         10<br>
       /    \<br>
      20    30<br>
    /   \<br>
   40  60<br>
Output: <br>
40 20 60 10 30<br>
Your Task:<br>
The task is to complete two functions serialize which takes the root node of the tree as input and stores the tree into an array and deSerialize which deserializes the array to the original tree and returns the root of it.<br>

Expected Time Complexity: O(Number of nodes).<br>
Expected Auxiliary Space: O(Number of nodes).<br>

Constraints:<br>
1 <= Number of nodes <= 10^4<br>
1 <= Data of a node <= 10^9<br>

__Intuition -> For serialisation , store the node's value in an array in Preorder fashion. For deserialisation , take out the values from the array and make nodes. First make node for root , then go for left subtree and then go for right subtree.__

```C++
void funS(Node* root,vector<int>&serial){
        if(root==NULL){
            serial.push_back(-1);
            return;
        }
        serial.push_back(root->data);
        funS(root->left,serial);
        funS(root->right,serial);
        return;
    }
    
    vector<int> serialize(Node *root) 
    {
        vector<int>serial;
        funS(root,serial);
        return serial;
    }
    
    
    //Function to deserialize a list and construct the tree.
    int index=0;
    Node * deSerialize(vector<int> &A)
    {
       if(index==A.size()){
           return NULL;
       }
       int val = A[index++];
       if(val==-1){
           return NULL;
       }
       
       Node* root = new Node(val);
       root->left = deSerialize(A);
       root->right = deSerialize(A);
       return root;
    }
```
