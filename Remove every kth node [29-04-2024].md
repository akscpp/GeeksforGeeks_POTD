[Problem Link](https://www.geeksforgeeks.org/problems/remove-every-kth-node/1)<br>
Given a singly linked list having n nodes, your task is to remove every kth node from the linked list.<br>

Example 1:<br>

Input:
n = 8<br>
linked list: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 <br>
k = 2<br>
Output: 
1 -> 3 -> 5 -> 7<br>
Explanation: <br>
After removing every 2nd node of the linked list, the resultant linked list will be: 1 -> 3 -> 5 -> 7.<br>
Example 2:<br>

Input:
n = 10<br>
linked list: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10 <br>
k = 3<br>
Output: <br>
1 -> 2 -> 4 -> 5 -> 7 -> 8 -> 10<br>
Explanation: <br>
After removing every 3rd node of the linked list, the resultant linked list will be: 1 -> 2 -> 4 -> 5 -> 7 -> 8 -> 10.<br>
Your Task:<br>
The task is to complete the function deleteK() which takes head of linked list and integer k as input parameters and delete every kth node from the linked list and return its head.<br>

Expected Time Complexity :  O(n)<br>
Expected Auxiliary Space :  O(1)<br>

Constraints:<br>
1 <= n <= 10^5<br>
-10^9 <= elements of linked list <= 10^9<br>
1 <= k <= n<br>

__Intuition -> Keep track of the count of nodes. When the count becomes divisible by k (if k is 2 , then 2 , 4 , 6 , 8, ... nodes are to be deleted), delete it.__

```C++
Node* deleteK(Node *head,int k){
      //Your code here
      if(k==1) return NULL;
      int num = 0;
      Node* prev = NULL;
      Node* p = head;
      
      while(p){
          num++;
          if(num%k==0){
              prev->next = p->next;
              delete p;
              p=prev->next;
          }
        else{
            prev=p;
            p=p->next;
        }
      }
      return head;
      
    }
```
