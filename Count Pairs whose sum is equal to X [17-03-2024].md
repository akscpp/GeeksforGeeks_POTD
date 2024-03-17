Given two linked list head1 and head2 with distinct elements, determine the count of all distinct pairs from both lists whose sum is equal to the given value x.

Note: A valid pair would be in the form (x, y) where x is from first linked list and y is from second linked list.<br>

Example 1:<br>

Input:
head1 = 1->2->3->4->5->6<br>
head2 = 11->12->13<br>
x = 15<br>
Output: 3<br>
Explanation: There are total 3 pairs whose sum is 15 : (4,11) , (3,12) and (2,13)<br>
Example 2:<br>

Input:<br>
head1 = 7->5->1->3<br>
head2 = 3->5->2->8<br>
x = 10<br>
Output: 2<br>
Explanation: There are total 2 pairs whose sum is 10 : (7,3) and (5,5)<br>
Your Task:<br>
You only need to implement the given function countPairs() that take two linked list head1 and head2 and return the count of distinct pairs whose sum is equal to x.<br>

Expected Time Complexity: O(length(head1)+lenght(head2)).<br>
Expected Auxiliary Space: O(length(head1)) or O(length(head2)).<br>

Constraints:<br>
1<=length(head1), lenght(head2)<=105<br>
1 <= Value of elements of  linked lists <= 10^9<br>
1<= x <= 10^9<br>
Note : All elements in each linked list are unique.<br>


__Intuition -> Use a set to store data of one list. Now , iterate over other to find the other pair .__

```C++
int countPairs(struct Node* head1, struct Node* head2, int x) {
        // Code here
        
        unordered_set<int>s;
        int cnt=0;
        Node* p = head1;
        while(p){
            s.insert(p->data);
            p=p->next;
        }
        
        Node* q =head2;
        
        while(q){
            if(s.find(x-q->data)!=s.end()){
                cnt++;
            }
            q=q->next;
        }
        return cnt;
        
    }
```
