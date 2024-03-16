You are given a node del_node of a Singly Linked List where you have to delete a value of the given node from the linked list but you are not given the head of the list.

By deleting the node value, we do not mean removing it from memory. We mean:<br>

The value of the given node should not exist in the linked list.<br>
The number of nodes in the linked list should decrease by one.<br>
All the values before & after the del_node node should be in the same order.<br>
Note:<br>

Multiple nodes can have the same values as the del_node, but you must only remove the node whose pointer del_node is given to you.<br>
It is guaranteed that there exists a node with a value equal to the del_node value and it will not be the last node of the linked list.<br>
Example 1:<br>

Input:<br>
Linked List = 1 -> 2<br>
del_node = 1<br>
Output: 
2<br>
Explanation: 
After deleting 1 from the linked list, 
we have remaining nodes as 2.<br>
Example 2:<br>

Input:<br>
Linked List = 10 -> 20 -> 4 -> 30<br>
del_node = 20<br>
Output: 
10 4 30<br>
Explanation: 
After deleting 20 from the linked list, 
we have remaining nodes as 10, 4, 30.<br>
Your Task:
You don't need to read or print anything. You only need to complete the function deleteNode() which takes a reference of the deleting node value & your task is to delete the given node value.<br>

Expected Time Complexity: O(1).<br>
Expected Auxilliary Space: O(1).<br>

Constraints:<br>
2 <= n <= 10^3  <br>
1 <= elements of the linked list <= 10^9<br>

__Intuition -> Replace the value of current pointed node with next node's value. Then point the next pointer of current node to next node's next.__

```C++
void deleteNode(Node *del_node)
    {
       // Your code here
       Node* p = del_node;
       p->data = p->next->data;
       p->next=p->next->next;
    }
```
