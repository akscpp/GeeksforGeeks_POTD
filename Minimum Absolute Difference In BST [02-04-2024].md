[Problem Link](https://www.geeksforgeeks.org/problems/minimum-absolute-difference-in-bst-1665139652/1)<br>
Given a binary search tree having n (n>1) nodes, the task is to find the minimum absolute difference between any two nodes.<br>

Example 1:<br>

Input:<br>
Input tree<br>

Output:
10<br>
Explanation:<br>
There are no two nodes whose absolute difference in smaller than 10.<br>
Example 2:<br>

Input:<br>
Input tree<br>

Output:
20<br>
Explanation:
There are no two nodes whose absolute difference in smaller than 20.<br>
Your Task:
You don't have to take any input. Just complete the function absolute_diff() , that takes root as input and return minimum absolute difference between any two nodes.<br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
2 <= n <= 10^5<br>
1 <= Node->data <= 10^9<br>

__Intuition-> Use a variable to store last visited node and with inorder traversal , keep finding the minimum absolute difference. Another solution is to store the inorder traversal in a vector and traverse it to find minimum absolute difference. (INORDER TRAVERSAL OF BST IS IN SORTED ORDER).__


```C++
int ans = 1e9;
    // void inorder(Node* root , vector<int>&ans){
    //     if(root==NULL) return ;
        
    //     inorder(root->left,ans);
    //     ans.push_back(root->data);
    //     inorder(root->right,ans);
    //     return;
    // }
    void solve(Node* root,int& last){
        if(root==NULL) return;
        solve(root->left,last);
        if(last!=-1){
            ans=min(ans,root->data-last);
        }
        last=root->data;
        solve(root->right,last);
        return;
    }
    
    int absolute_diff(Node *root)
    {
        //Your code here
        // vector<int>ans;
        // inorder(root,ans);
        // int mini=1e9;
        
        // for(int i=0;i<ans.size()-1;i++){
        //     mini = min(mini,abs(ans[i]-ans[i+1]));
        // }
        // return mini;
        int last = -1;
        solve(root,last);
        
        return ans;
    }
```
