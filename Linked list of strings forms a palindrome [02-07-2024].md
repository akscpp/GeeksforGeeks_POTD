[Problem Link](https://www.geeksforgeeks.org/problems/linked-list-of-strings-forms-a-palindrome/1)<br>
Given a linked list with string data, check whether the combined string formed is palindrome. If the combined string is palindrome then return true otherwise return false.<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/a6c17b6c-02b0-4e39-9352-fc526b5120a5)
<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/74fea20a-d76d-407f-a2ba-41423253428f)
<br>
Expected Time Complexity:  O(n)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
1 <= Node.data.length<= 10^3<br>
1<=list.length<=10^3<br>

__Intuition ->Extract the string from linkedlist by traversing. After that, check for palindrome.__

```C++
bool compute(Node* head) {
        // Your code goes here
        Node* p = head;
        string s = "";
        
        while(p){
            s+=(p->data);
            p=p->next;
        }
        
        string original = s;
        reverse(s.begin(),s.end());
        
        return (original==s);
    }
```
