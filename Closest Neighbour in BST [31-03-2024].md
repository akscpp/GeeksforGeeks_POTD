[Problem Link](https://www.geeksforgeeks.org/problems/closest-neighbor-in-bst/1)<br>
Given the root of a binary search tree and a number n, find the greatest number in the binary search tree that is less than or equal to n. <br>

Example 1 :<br>

Input : 

n = 24<br>
Output : 
21<br>

Explanation : The greatest element in the tree which 
              is less than or equal to 24, is 21. <br>
              (Searching will be like 5->12->21)<br>
Example 2 :<br>

Input : <br>

n = 4<br>
Output : <br>
3<br>
Explanation : The greatest element in the tree which 
              is less than or equal to 4, is 3. <br>
              (Searching will be like 5->2->3)<br>
Your task :<br>
You don't need to read input or print anything. Your task is to complete the function findMaxForN() which takes the root of the BST, and the integer n as input paramters and returns the greatest element less than or equal to n in the given BST.<br>

Expected Time Complexity: O(Height of the BST)<br>
Expected Auxiliary Space: O(Height of the BST).<br>

Constraints:
1 <= n <= 10^3<br>

__Intuition-> We have to find the greatest number in the tree which is <= n . So, when we encounter a value <=n , then we store it and move to right subtree (since BST). If the node value > n , then we move to left subtree.__

```C++
void f(Node* root, int& maxi , int n){
        if(root==NULL) return ;
        if(root->key<=n){
            maxi = root->key;
            f(root->right,maxi,n);
        }else{
            f(root->left,maxi,n);
        }
    }
    int findMaxForN(Node* root, int n) {
        // code here
        int maxi=-1;
        f(root,maxi,n);
        return maxi;
    }
```
