You are given a Linked list of size n. The list is in alternating ascending and descending orders. Sort the given linked list in non-decreasing order.<br>

Example 1:<br>

Input:
n = 6<br>
LinkedList = 1->9->2->8->3->7<br>
Output: 1 2 3 7 8 9<br>
Explanation: 
After sorting the given list will be 1->2->3->7->8->9.<br>
Example 2:<br>

Input:
n = 5<br>
LinkedList = 13->99->21->80->50<br>
Output: 13 21 50 80 99<br>
Explanation:
After sorting the given list will be 13->21->50->80->99.<br>
Your Task:
You do not need to read input or print anything. The task is to complete the function sort() which should sort the linked list of size n in non-decreasing order. <br>

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
1 <= Number of nodes <= 100<br>
0 <= Values of the elements in linked list <= 10^3<br>

__Intuition -> Separate the linkedList into two lists , one with ascending and other with descending order. Reverse the descending order list and merge both the lists.__

```C++
Node* reverse(Node* head){
     if(head==NULL || head->next==NULL) return head;
     Node* tmp=reverse(head->next);
     head->next->next=head;
     head->next=NULL;
     return tmp;
 }
 Node* merge(Node* l1,Node* l2){
     if(!l1) return l2;
     if(!l2) return l1;
     if(l1->data<=l2->data){
         l1->next=merge(l1->next,l2);
         return l1;
     }
     else{
         l2->next=merge(l1,l2->next);
         return l2;
     }
 }
 void sort(Node **head)
 {
      // Code here
       
      Node* i=*head;
      Node* d=i->next;
      Node* dc=d;
      while(d && d->next){
          i->next=i->next->next;
          d->next=d->next->next;
          i=i->next;
          d=d->next;
      }
      i->next=NULL;
      *head=merge(*head,reverse(dc));
 }
```

