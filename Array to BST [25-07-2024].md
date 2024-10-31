[Problem Link](https://www.geeksforgeeks.org/problems/array-to-bst4443/1)<br>

Given a sorted array. Convert it into a Height Balanced Binary Search Tree (BST). Return the root of the BST.<br>

Height-balanced BST means a binary tree in which the depth of the left subtree and the right subtree of every node never differ by more than 1.<br>

Note: The driver code will check the BST, if it is a Height-balanced BST, the output will be true otherwise the output will be false.<br>

![image](https://github.com/user-attachments/assets/0aa7cc1d-7ed8-4a1b-bbd5-ca33b9555de2)<br>


Expected Time Complexity: O(n)<br>
Expected Auxillary Space: O(n)<br>

Constraints:<br>

1 ≤ nums.size() ≤ 10^5<br>
1 ≤ nums[i] ≤ 10^5<br>


__Intuition ->Since the array is sorted , it is inorder traversal of BST.SO , use divide and conquer and find the middle element of the array which will be the root.__
```C++
Node* buildBST(vector<int>& nums, int start , int end){
        if(start>end) return NULL;
        
        int mid = start + (end - start)/2;
        
        Node* node = new Node(nums[mid]);
        node->left = buildBST(nums,start,mid-1);
        node->right = buildBST(nums,mid+1,end);
        
        return node;
    }
    Node* sortedArrayToBST(vector<int>& nums) {
        Node* root = buildBST(nums,0,nums.size()-1);
        return root;
    }
```
