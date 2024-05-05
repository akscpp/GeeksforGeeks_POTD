[Problem Link](https://www.geeksforgeeks.org/problems/vertical-sum/1)<br>

Given a binary tree having n nodes, find the vertical sum of the nodes that are in the same vertical line. Return all sums through different vertical lines starting from the left-most vertical line to the right-most vertical line.<br>

Example 1:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/74e6bc1c-5d69-4147-a438-5ef1c10569e8)

Example 2:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/b2ea063b-b156-4c1e-96e4-5051742105b4)

Your Task:
You don't need to take input. Just complete the function verticalSum() that takes root node of the tree as parameter and returns an array containing the vertical sum of tree from left to right.<br>

Expected Time Complexity: O(nlogn).<br>
Expected Auxiliary Space: O(n).<br>

Constraints:<br>
1<=n<=10^4<br>
1<= Node value <= 10^5<br>

__Intuition -> Use BFS. When storing the nodes in queue , also store their corresponding vertical level (root=0 , root left = 0 - 1 . root right = 0 + 1.Store these in map. This will sum the nodes at same vertical level.__

```C++
vector <int> verticalSum(Node *root) {
        // add code here.
        map<int,int>mp;
        queue<pair<Node*,int>>q;
        
        q.push({root,0});
        
        while(!q.empty()){
            pair<Node*,int>p = q.front();
            q.pop();
            
            Node* curr = p.first;
            int lvl = p.second;
            
            mp[lvl]+=curr->data;
            
            if(curr->left!=NULL) q.push({curr->left,lvl-1});
            
            if(curr->right!=NULL) q.push({curr->right,lvl+1});
        }
        
        vector<int>ans;
        
        for(auto it:mp){
            ans.push_back(it.second);
        }
        return ans;
    }
```
