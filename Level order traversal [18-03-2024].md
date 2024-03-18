Given a root of a binary tree with n nodes, find its level order traversal.<br>
Level order traversal of a tree is breadth-first traversal for the tree.<br>

Example 1:<br>

Input:<br>
    1<br>
  /   \ <br>
 3     2<br>
Output:
1 3 2<br>
Example 2:<br>

Input:<br>
        10<br>
     /      \<br>
    20       30<br>
  /   \<br>
 40   60<br>
Output:
10 20 30 40 60<br>
Your Task:<br>
You don't have to take any input. Complete the function levelOrder() that takes the root node as input parameter and returns a list of integers containing the level order traversal of the given Binary Tree.<br>



Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 ≤ n ≤ 10^5<br>
0 ≤ Data of a node ≤ 10^9<br>

__Intuition-> Use queue to store all the nodes one by one. If at node x , first push its left child , then push its right child. One by one , pop out and store the values.__


```C++
vector<int> levelOrder(Node* root)
    {
      //Your code here
      vector<int>ans;
      queue<Node*>q;
      q.push(root);
      
      while(!q.empty()){
          Node* curr = q.front();
          q.pop();
          ans.push_back(curr->data);
          
          if(curr->left!=NULL) q.push(curr->left);
          if(curr->right!=NULL) q.push(curr->right);
      }
      return ans;
      
    }
```
