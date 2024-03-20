[Problem Link](https://www.geeksforgeeks.org/problems/sum-of-the-longest-bloodline-of-a-tree/1)<br>

Given a binary tree having n nodes. Find the sum of all nodes on the longest path from root to any leaf node. If two or more paths compete for the longest path, then the path having maximum sum of nodes will be considered.<br>

Example 1:<br>

Input: <br>
        4   <br>     
       /  \   <br>    
      2   5     <br> 
     / \   /  \  <br>   
    7  1 2  3    <br>
      /<br>
     6<br>
Output: <br>
13<br>
Explanation:<br>
        4        <br>
       /  \      <br> 
      2   5      <br>
     / \   /  \   <br>  
    7  1 2  3 <br>
      /<br>
     6<br>
The highlighted nodes (4, 2, 1, 6) above are part of the longest root to leaf path having sum = (4 + 2 + 1 + 6) = 13<br>
Example 2:<br>

Input: <br>
          1<br>
        /   \<br>
       2    3<br>
      / \    /  \<br>
     4   5 6   7<br>
Output: <br>
11<br>
Explanation:<br>
Use path 1->3->7, with sum 11.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function sumOfLongRootToLeafPath() which takes root node of the tree as input parameter and returns an integer denoting the sum of the longest root to leaf path of the tree.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 <= n <= 10^5<br>
0 <= data of each node <= 10^4<br>




__Intuition -> We will use a queue to detect max sum using level order traversal. Since the queue will always contain nodes at a level. So , we can detect the max sum from these sum. Considering the case when the tree contains a longest path of height 4 , then during that time , the queue will contain the node at the height = 4 only.__

```C++
int sumOfLongRootToLeafPath(Node *root)
    {
        //code here
        queue<pair<Node*,int>>q;
        
        q.push({root,root->data});
        int maxi=0;
        while(!q.empty()){
            int cnt = q.size();
            maxi=0;
            for(int i=0;i<cnt;i++){
                pair<Node*,int> p = q.front();
                q.pop();
                Node* curr = p.first;
                int sum = p.second;
                maxi=max(maxi,sum);
                if(curr->left!=NULL) q.push({curr->left,sum+curr->left->data});
                if(curr->right!=NULL) q.push({curr->right,sum+curr->right->data});
            }
            
        }
        
        return maxi;
        
        
    }
```
