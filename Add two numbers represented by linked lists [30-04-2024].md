[Problem Link](https://www.geeksforgeeks.org/problems/add-two-numbers-represented-by-linked-lists/1)<br>
Given two decimal numbers, num1 and num2, represented by linked lists of size n and m respectively. The task is to return a linked list that represents the sum of these two numbers.<br>

For example, the number 190 will be represented by the    linked list, 1->9->0->null, similarly 25 by 2->5->null. Sum of these two numbers is 190 + 25 = 215, which will be represented by 2->1->5->null. You are required to return the head of the linked list 2->1->5->null.<br>

Note: There can be leading zeros in the input lists, but there should not be any leading zeros in the output list.<br>







Example 1:<br>

Input:<br>
n = 2<br>
num1 = 45 (4->5->null)<br>
m = 3<br>
num2 = 345 (3->4->5->null)<br>
Output: <br>
3->9->0->null  <br>
Explanation: <br>
For the given two linked list (4 5) and (3 4 5), after adding the two linked list resultant linked list will be (3 9 0).<br>
Example 2:<br>

Input:<br>
n = 4<br>
num1 = 0063 (0->0->6->3->null)<br>
m = 2<br>
num2 = 07 (0->7->null)<br>
Output: <br>
7->0->null<br>
Explanation: <br>
For the given two linked list (0 0 6 3) and (0 7), after adding the two linked list resultant linked list will be (7 0).<br>
Your Task:<br>
The task is to complete the function addTwoLists() which has node reference of both the linked lists and returns the head of the sum list. <br>

Expected Time Complexity: O(n+m)<br>
Expected Auxiliary Space: O(max(n,m)) for the resultant list.<br>

Constraints:<br>
1 <= n, m <= 10^4<br>

__Intuition ->Reverse both the list and add the value. Now , sum/10 will give carry and sum/10 will give remainder. Store remainder in a new node and move to next node keeping the carry.__

```C++
Node* reverseList(Node* head){
        if(head==NULL || head->next==NULL) return head;
        
        Node* p = head;
        Node* q = NULL;
        
        while(p){
            Node* nxt = p->next;
            p->next=q;
            q=p;
            p=nxt;
        }
        return q;
    }
    struct Node* addTwoLists(struct Node* num1, struct Node* num2)
    {
        // code here
        Node* p = reverseList(num1);
        Node* q = reverseList(num2);
        
        Node* dummy = new Node(-1);
        Node* dH = dummy;
        Node* tail = dummy;
        
        int carry=0;
        while(p || q){
            int sum=0;
            if(p!=NULL){
                sum+=p->data;
                p=p->next;
            } 
            
            if(q!=NULL){
                sum+=q->data;
                q=q->next;
            }
            
            if(carry>0){
                sum+=carry;
            }
            
            carry = sum/10;
            int rem = sum%10;
            
            Node* temp = new Node(rem);
            tail->next=temp;
            tail=temp;
            
        }
        
        if(carry>0){
            Node* temp= new Node(carry);
            
            tail->next=temp;
            tail=temp;
        }
        dH=dH->next;
        Node* head1 = reverseList(dH);
        Node* l = head1;
        
        while(l){
            if(l->data==0){
                l=l->next;
            }else{
                break;
            }
        }
        
        if(l==NULL){
            Node* temp = new Node(0);
            return temp;
        }
        return l;
    }
```
