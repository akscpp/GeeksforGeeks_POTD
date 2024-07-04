[Problem Link](https://www.geeksforgeeks.org/problems/duplicate-subtrees/1)<br>

Given a binary tree, your task is to find all duplicate subtrees from the given binary tree.<br>

Duplicate Subtree : Two trees are duplicates if they have the same structure with the same node values.<br>

Note:  Return the root of each tree in the form of a list array & the driver code will print the tree in pre-order tree traversal in lexicographically increasing order.<br>

Examples:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/bef6daa8-c616-4c42-bdb9-811d6de6f954)
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/1dca8779-577d-42a0-8677-1337b818806d)
<br>
Expected Time Complexity: O(n)<br>
Expected Space Complexity: O(n)<br>

Constraints:<br>
1<= size of binary tree <=100<br>

__Intuition-> Use a  string to include the root value and the serialized strings of its left and right subtrees. A map is used to count occurrences of each serialized subtree. When a subtree is encountered for the second time (i.e., its count in the hashmap becomes 1), the root node of this subtree is added to the result list.__

```C++
string help(Node* root, vector<Node*>& ans, unordered_map<string,int>& mp){
        if(root==NULL) return "#";
        
        string temp = to_string(root->data)+' '+help(root->left,ans,mp)+' '+help(root->right,ans,mp);
        if(mp[temp]==1){
            ans.push_back(root);
        }
        mp[temp]++;
        return temp;
    }
    vector<Node*> printAllDups(Node* root) {
        vector<Node*>ans;
        unordered_map<string,int>mp;
        help(root,ans,mp);
        return ans;
    }
```
