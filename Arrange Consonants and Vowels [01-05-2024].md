[Problem Link](https://www.geeksforgeeks.org/problems/arrange-consonants-and-vowels/1)<br>

Given a singly linked list having n nodes containing english alphabets ('a'-'z'). Rearrange the linked list in such a way that all the vowels come before the consonants while maintaining the order of their arrival. <br>

Example 1:<br>

Input:
n = 9<br>
linked list: a -> b -> c -> d -> e -> f -> g -> h -> i <br>
Output: <br>
a -> e -> i -> b -> c -> d -> f -> g -> h<br>
Explanation: 
After rearranging the input linked list according to the condition the resultant linked list will be as shown in output.<br>
Example 2:<br>

Input:
n = 8<br>
linked list: a -> b -> a -> b -> d -> e -> e -> d <br>
Output: 
a -> a -> e -> e -> b -> b -> d -> d<br>
Explanation: 
After rearranging the input linked list according to the condition the resultant linked list will be as shown in output.<br>
Your Task:
Your task is to complete the function arrangeCV(), which takes head of linked list and arranges the list in such a way that all the vowels come before the consonants while maintaining the order of their arrival and returns the head of the updated linked list.<br>

Expected Time Complexity :  O(n)<br>
Expected Auxiliary Space :  O(1)<br>

Constraints:
1 <= n <= 10^4<br>
'a' <= elements of linked list <= 'z'<br>

__Intuition -> Use 4 pointers to keep start where vowel starts , vowel ends ,  consonants starts , consonants end. After that , whenever a vowel is encountered , point vowel end to that . Similarly , do for consonants. At last , point vowel end to consonant start.__

```C++
bool isVowel(char c){
        if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u'){
            return true;
        }
        return false;
    }
    struct Node* arrangeCV(Node* head) {
        // Code here
        if(head==NULL || head->next==NULL){
            return head;
        }
        
        Node* vs = NULL;
        Node* ve = NULL;
        Node* cs = NULL; 
        Node* ce = NULL;
        
        Node* p = head;
        Node* q = head;
        
        while(p){
            if(isVowel(p->data)){
                if(vs==NULL){
                    vs=p;
                    ve=p;
                }else{
                    ve->next=p;
                    ve=p;
                }
                
            }else{
                if(cs==NULL){
                    cs=p;
                    ce=p;
                }else{
                    ce->next=p;
                    ce=p;
                }
                 
            }
             p=p->next;
           
        }
        
        if(vs==NULL) return cs;
        if(cs==NULL) return vs;
        
        ve->next=cs;
        ce->next=NULL;
        return vs;
    }
```
