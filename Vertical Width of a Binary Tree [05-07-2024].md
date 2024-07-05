[Problem Link](https://www.geeksforgeeks.org/problems/vertical-width-of-a-binary-tree/1)<br>

Given a Binary Tree. You need to find and return the vertical width of the tree.
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/f79f6ab1-a90c-43e7-ab05-8aeda05068aa)

<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/98ea0041-1b0f-4054-8642-14a66772be2e)

Expected Time Complexity: O(n).
Expected Auxiliary Space: O(height of the tree).

Constraints:
0 <= number of nodes <= 10^4

__Intuition ->Use BFS. Start with storing the root along with 1. If left child , insert distance-1 and for right , use distance+1. Find max and min out of all these distances and return width.__

```C++
int verticalWidth(Node* root) {
        if(root==NULL) return 0;
        
        queue<pair<Node*,int>>q;
        q.push({root,1});
        int mini=1e9;
        int maxi = -1e9;
        
        while(!q.empty()){
            pair<Node*,int>p = q.front();
            q.pop();
            
            Node* curr = p.first;
            int dist= p.second;
            
            mini = min(mini,dist);
            maxi = max(maxi,dist);
            
            if(curr->left!=NULL){
                q.push({curr->left,dist-1});
            }
            if(curr->right!=NULL){
                q.push({curr->right,dist+1});
            }
        }
        
        return maxi-mini+1;
    }
```
