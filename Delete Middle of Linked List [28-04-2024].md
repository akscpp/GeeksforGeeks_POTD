[Problem Link](https://www.geeksforgeeks.org/problems/delete-middle-of-linked-list/1)<br>
Given a singly linked list, delete middle of the linked list. For example, if given linked list is 1->2->3->4->5 then linked list should be modified to 1->2->4->5.<br>
If there are even nodes, then there would be two middle nodes, we need to delete the second middle element. For example, if given linked list is 1->2->3->4->5->6 then it should be modified to 1->2->3->5->6.<br>
If the input linked list has single node, then it should return NULL.

Example 1:<br>

Input:<br>
LinkedList: 1->2->3->4->5<br>
Output: <br>
1 2 4 5<br>
Example 2:<br>

Input:<br>
LinkedList: 2->4->6->7->5->1<br>
Output: <br>
2 4 6 5 1<br>
Your Task:<br>
The task is to complete the function deleteMid() which takes head of the linkedlist  and return head of the linkedlist with middle element deleted from the linked list. If the linked list is empty or contains single element then it should return NULL.<br>

Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
1 <= n <= 10^5<br>
1 <= value[i] <= 10^9<br>

__Intuition -> Use fast and slow pointer.Move slow by one and fast by two. At the end of loop , slow will point to middle node. Also , keep track of previous node while traversing the list. Point previous node next to middle node next.__

```C++
Node* deleteMid(Node* head)
    {
        // Your Code Here
        if(head==NULL || head->next==NULL) return NULL;
        
        Node* slow = head , *fast=head;
        Node* temp = NULL;
        while(fast && fast->next){
            temp = slow;
            slow = slow ->next;
            fast=fast->next;
            if(fast!=NULL) fast=fast->next;
        }
        temp->next=slow->next;
        return head;
    }
```
