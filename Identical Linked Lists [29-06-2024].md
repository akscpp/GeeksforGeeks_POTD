[Problem Link](https://www.geeksforgeeks.org/problems/identical-linked-lists/1)<br>

Given the two singly Linked Lists respectively. The task is to check whether two linked lists are identical or not. <br>
Two Linked Lists are identical when they have the same data and with the same arrangement too. If both Linked Lists are identical then return true otherwise return false. <br>

Examples:<br>

Input:<br>
LinkedList1: 1->2->3->4->5->6<br>
LinkedList2: 99->59->42->20<br>
Output: false<br>
Explanation:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/b5b14e24-ee16-45c6-8fd6-a9611979baf2)

As shown in figure linkedlists are not identical.<br>
Input:<br>
LinkedList1: 1->2->3->4->5<br>
LinkedList2: 1->2->3->4->5<br>
Output: true<br>
Explanation: <br>
 ![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/7a429b9c-7b24-44e4-9427-e581de6da119)

As shown in figure both are identical.<br>
Expected Time Complexity: O(n)<br>
Expected Auxilliary Space: O(1)<br>

Constraints:<br>
1 <= length of lists <= 10^3<br>

__Intuition ->Compare both linkedList by traversing them.__

```C++
bool areIdentical(struct Node *head1, struct Node *head2) {
    // Code here
    Node* p = head1;
    Node* q = head2;
    
    while(p && q){
        if(p->data!=q->data){
            return false;
        }
        p=p->next;
        q=q->next;
    }
    
    if(p!=NULL || q!=NULL) return false;
    return true;
}
```
