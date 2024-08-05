[Problem Link](https://www.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1)<br>

Given a binary tree, return an array where elements represent the bottom view of the binary tree from left to right.<br>

Note: If there are multiple bottom-most nodes for a horizontal distance from the root, then the latter one in the level traversal is considered. For example, in the below diagram, 3 and 4 are both the bottommost nodes at a horizontal distance of 0, here 4 will be considered.<br>

![image](https://github.com/user-attachments/assets/993a5fcc-57d4-4240-b2c3-1c88c230d038)<br>


Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 <= Number of nodes <= 10^5<br>
1 <= Data of a node <= 10^5<br>

__Intuition ->Store node along with its horizontal distance from the root in a map. For horizontal distance with multiple nodes, store the latest one (keep over-writing). At last, collect all the nodes from the map.__<br>

```C++
vector <int> bottomView(Node *root) {
        if(root==NULL) return {};
        map<int,int>mp;
        queue<pair<Node*,int>>q;
        q.push({root,0});
        
        while(!q.empty()){
            pair<Node*,int> p = q.front();
            q.pop();
            int val = p.first->data;
            int hd = p.second;
            mp[hd]=val;
            
            if(p.first->left!=NULL){
                q.push({p.first->left,hd-1});
            }
            if(p.first->right!=NULL){
                q.push({p.first->right,hd+1});
            }
        }
        vector<int>vec;
        for(auto &it:mp){
            vec.push_back(it.second);
        }
        return vec;
    }
```
