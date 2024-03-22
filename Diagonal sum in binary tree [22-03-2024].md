[Problem Link](https://www.geeksforgeeks.org/problems/diagonal-sum-in-binary-tree/1)

Consider Red lines of slope -1 passing between nodes (in following diagram). The diagonal sum in a binary tree is the sum of all node datas lying between these lines. Given a Binary Tree of size n, print all diagonal sums.<br>

For the following input tree, output should be 9, 19, 42.<br>
9 is sum of 1, 3 and 5.<br>
19 is sum of 2, 6, 4 and 7.<br>
42 is sum of 9, 10, 11 and 12.<br>

DiagonalSum<br>

Example 1:<br>

Input:<br>
         4<br>
       /   \<br>
      1     3<br>
           /<br>
          3<br>
Output: 
7 4 <br>
Example 2:<br>

Input:<br>
           10<br>
         /    \<br>
        8      2<br>
       / \    /<br>
      3   5  2<br>
Output: <br>
12 15 3 <br>
Your Task:<br>
You don't need to take input. Just complete the function diagonalSum() that takes root node of the tree as parameter and returns an array containing the diagonal sums for every diagonal present in the tree with slope -1.<br>

Expected Time Complexity: O(nlogn).<br>
Expected Auxiliary Space: O(n).<br>

Constraints:<br>
1 <= n <= 10^5<br>
0 <= data of each node <= 10^4<br>


__Intuition -> We can use dfs to traverse the nodes in one diagonal . First traverse right subtree keeping the level same . Then , when traversing the left subtree , increment level by 1. This will ensure that the same diagonal nodes are added. We can use a vector of size  10^5 (as given in constraints) to store the sum . Why 10^5  ? Suppose we get  a left skewed tree with number of nodes = 10^5. So , in this case , each node will be in a different diagonal. So , this will give 10^5 diagonals.__

```C++
void dfs(Node* node,int currLevel , vector<int>&levels){
        if(node==NULL) return;
        levels[currLevel]+=node->data;
        dfs(node->right,currLevel,levels);
        dfs(node->left,currLevel+1,levels);
    }
    vector<int> diagonalSum(Node* root) {
        // Add your code here
        vector<int>levels(100001,0);
        dfs(root,0,levels);
        vector<int>ans;
        for(int i=0;i<levels.size();i++){
            if(levels[i]!=0){
                ans.push_back(levels[i]);
            }
        }
        return ans;
        
    }
```
