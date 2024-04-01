[Problem Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1)<br>
Given a binary tree with n nodes, find the number of pairs violating the BST property.<br>
BST has the following properties:-<br>

Every node is greater than its left child and less than its right child.<br>
Every node is greater than the maximum value of in its left subtree and less than the minimum value in its right subtree.<br>
The maximum in the left sub-tree must be less than the minimum in the right subtree.<br>
Example 1:<br>

Input : <br>
n = 5<br>
Input tree<br>
    
Output :<br>
5<br>
Explanation :<br> 
Pairs violating BST property are:-<br>
(10,50), 10 should be greater than its left child value.<br>
(40,30), 40 should be less than its right child value.<br>
(50,20), (50,30) and (50,40), maximum of left subtree of 10 is 50 greater than 20, 30 and 40 of its right subtree.<br>
Example 2:<br>

Input : 
n = 6<br>
Input tree<br>

Output :
8<br>
Explanation :<br>
There are total 8 Pairs which violation the BST properties.<br>
Your task :<br>
You don't have to read input or print anything. Your task is to complete the function pairsViolatingBST() that takes the root of the tree and n as input and returns number of pairs violating BST property.<br>
 
Expected Time Complexity: O(n*logn)<br>
Expected Space Complexity: O(n)<br>
 
Your Task :<br>
1 <= n <= 2*10^4<br>
-109 <= node->data <= 10^9<br>


__Intuition->We will proceed with finding the inoreder traversalof the BST. The inorder traversal of BST is sorted in non descending order. Now , we can count the pairs violating the ascending order rule using count Inversions.__

```C++
void inorder(Node* root,vector<int>& nums){
        if(root==NULL) return;
        
        inorder(root->left,nums);
        nums.push_back(root->data);
        inorder(root->right,nums);
        return ;
    }
    void merge(int low,int mid,int high,vector<int>&nums,int& cnt){
        int j = mid+1;
        for(int i=low;i<=mid;i++){
            while(j<=high && nums[i]>nums[j]){
                j++;
            }
            cnt+=j-(mid+1);
        }
        int size = high-low+1;
        vector<int>temp(size,0);
        int i=low;
        j=mid+1;
        int k=0;
        
        while(i<=mid && j<=high){
            if(nums[i]<=nums[j]){
                temp[k++]=nums[i++];
            }else {
                temp[k++]=nums[j++];
                
            }
        }
        
        
        while(i<=mid){
            temp[k++]=nums[i++];
        }
        
        while(j<=high){
            temp[k++]=nums[j++];
        }
        int m=0;
        for(int i=low;i<=high;i++){
            nums[i]=temp[m++];
        }
    }
    void mergeSort(int low,int high,vector<int>&nums,int& cnt){
        if(low<high){
            int mid= low+(high-low)/2;
            mergeSort(low,mid,nums,cnt);
            mergeSort(mid+1,high,nums,cnt);
            merge(low,mid,high,nums,cnt);
        }
    }

    /*You are required to complete below function */
    int pairsViolatingBST(int n, Node* root) {
    int cnt = 0;
    vector<int> nums; 
    inorder(root, nums); 
    mergeSort(0, nums.size() - 1, nums, cnt); 
    return cnt;
}
```
