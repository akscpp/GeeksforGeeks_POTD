[Problem Link](https://www.geeksforgeeks.org/problems/zigzag-tree-traversal/1)<br>

Given a binary tree with n nodes. Find the zig-zag level order traversal of the binary tree.<br>

Example 1:<br>

Input:<br>
        1<br>
      /   \<br>
     2    3<br>
    / \    /   \<br>
   4   5 6   7<br>
Output:<br>
1 3 2 4 5 6 7<br>
Example 2:<br>

Input:<br>
           7<br>
        /     \<br>
       9      7<br>
     /  \      / <br>  
    8   8  6 <br>    
   /  \ <br>
  10  9 <br>
Output:<br>
7 7 9 8 8 6 9 10 <br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function zigZagTraversal() which takes the root node of the Binary Tree as its input and returns a list containing the node values as they appear in the zig-zag level-order traversal of the tree.<br>

Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(n).<br>

Constraints:<br>
1 <= n <= 10^5<br>

__Intuition -> We will use level order traversal to store nodes at a level (initialised as 1). If level is even then we reverse the nodes in temp array and store in our resultant array. If level is odd , then we store the contents of temp array without reversing them.__

```C++
vector <int> zigZagTraversal(Node* root)
    {
    	// Code here
    	queue<Node*>q;
    	q.push(root);
    	int level=1;
    	vector<int>ans;
    	while(!q.empty()){
    	    int cnt = q.size();
    	    vector<int>temp;
    	    for(int i=0;i<cnt;i++){
    	        Node* curr = q.front();
    	        q.pop();
    	        temp.push_back(curr->data);
    	        
    	        if(curr->left!=NULL) q.push(curr->left);
    	        if(curr->right!=NULL) q.push(curr->right);
    	        
    	    }
    	    
    	    if(level%2==0){
    	        reverse(temp.begin(),temp.end());
    	    }
    	    for(int i=0;i<temp.size();i++){
    	        ans.push_back(temp[i]);
    	    }
    	    level++;
    	    
    	}
    	return ans;
    }
```
