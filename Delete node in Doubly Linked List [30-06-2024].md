[Problem Link](https://www.geeksforgeeks.org/problems/delete-node-in-doubly-linked-list/1)<br>

Given a doubly Linked list and a position. The task is to delete a node from a given position (position starts from 1) in a doubly linked list and return the head of the doubly Linked list.<br>

Examples:<br>

Input: LinkedList = 1 <--> 3 <--> 4, x = 3<br>
Output: 1 3  <br>
Explanation: <br>
After deleting the node at position 3 (position starts from 1),the linked list will be now as 1 <--> 3.<br>
 
Input: LinkedList = 1 <--> 5 <--> 2 <--> 9, x = 1<br>
Output: 5 2 9<br>
Explanation:<br>

Expected Time Complexity: O(n)<br>
Expected Auxilliary Space: O(1)<br>

Constraints:<br>
2 <= size of the linked list(n) <= 10^5<br>
1 <= x <= n<br>
1 <= node.data <= 10^9<br>

__Intuition ->Go to the node which is to be deleted and change the links.__

```C++
Node* deleteNode(Node* head, int x) {
        // Your code here
        if(x==1){
            Node* p = head;
            p=p->next;
            p->prev=NULL;
            delete head;
            return p;
        }
        
        Node*p = head;
        for(int i=1;i<x;i++){
            p=p->next;
        }
        
        Node* q = p->prev;
        Node* r = p->next;
        
        q->next = r;
        if(r!=NULL)
            r->prev = q;
        delete p;
        return head;
    }
```
