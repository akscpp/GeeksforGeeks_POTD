[Problem Link](https://www.geeksforgeeks.org/problems/minimum-element-in-bst/1)<br>
Given the root of a Binary Search Tree. The task is to find the minimum valued element in this given BST.<br>

Example 1:<br>

Input:<br>
           5<br>
         /    \<br>
        4      6<br>
       /        \<br>
      3          7<br>
     /<br>
    1<br>
Output: 1<br>
Example 2:<br>

Input:<br>
             9<br>
              \<br>
               10<br>
                \<br>
                 11<br>
Output: 9<br>
Your Task:<br>
The task is to complete the function minValue() which takes root as the argument and returns the minimum element of BST. If the tree is empty, there is no minimum element, so return -1 in that case.<br>

Expected Time Complexity: O(Height of the BST)<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
0 <= n <= 10^4<br>


__Intuition -> In a BST , minimum element is the left child. So , we go to left of tree for finding minimum value. If tree is right skewed , return root.__

```C++
int minValue(Node* root) {
        // Code here
        if(root==NULL) return -1;
        if(root->left==NULL){
            return root->data;
        }
        return minValue(root->left);
    }
```
