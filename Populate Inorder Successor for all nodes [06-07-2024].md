[Problem Link](https://www.geeksforgeeks.org/problems/populate-inorder-successor-for-all-nodes/1)<br>

Given a Binary Tree, complete the function to populate the next pointer for all nodes. The next pointer for every node should point to the Inorder successor of the node.
You do not have to return or print anything. Just make changes in the root node given to you.<br>

Note: The node having no in-order successor will be pointed to -1. You don't have to add -1 explicitly, the driver code will take care of this.<br>

![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/436b580a-cf18-484d-9619-1683b9b7fc36)
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/e87f190c-a525-4877-9ea1-3743261d3c6b)

Expected Time Complexity: O(n)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1<= no. of nodes <=10^5<br>
1<= data of the node <=10^5<br>
