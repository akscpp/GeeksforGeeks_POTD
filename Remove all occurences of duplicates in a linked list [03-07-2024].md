[Problem Link](https://www.geeksforgeeks.org/problems/remove-all-occurences-of-duplicates-in-a-linked-list/1)<br>

Given a sorted linked list, delete all nodes that have duplicate numbers (all occurrences), leaving only numbers that appear once in the original list, and return the head of the modified linked list. 

Examples:
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/a943f1cc-fc33-4847-86d0-ad785b7fe5be)
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/0fe55e94-b3fb-420d-b537-9ff9cc67e9c8)
<br>
Expected Time Complexity: O(n)
Expected Auxiliary Space: O(1)
Constraints:
1 ≤ size(list) ≤ 10^5

__Intuition ->Store count of numbers in a map. Now , include only those nodes in the answer which has the number whose count is 1.__

```C++
Node* removeAllDuplicates(struct Node* head) {
        unordered_map<int,int>mp;
        Node* p = head;

        while(p){
            mp[p->data]++;
            p=p->next;
        }

        Node* dummyNode = new Node(-1);
        Node* temp = dummyNode;

        p=head;

        while(p){
            if(mp[p->data]==1){
                temp->next = p;
                temp=p;
                p=p->next;
            }
            else{
                p=p->next;
            }
        }
        temp->next=NULL;
        if(temp==dummyNode) return NULL;

        return dummyNode->next;
    }
```
