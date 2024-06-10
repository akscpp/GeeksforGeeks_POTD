[Problem Link](https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1)<br>
Given a set of n nuts & bolts. There is a one-on-one mapping between nuts and bolts. You have to Match nuts and bolts efficiently. Comparison of a nut to another nut or a bolt to another bolt is not allowed. It means the nut can only be compared with the bolt and the bolt can only be compared with the nut to see which one is bigger/smaller.<br>
The elements should follow the following order: { !,#,$,%,&,*,?,@,^ }<br>

Note: Make all the required changes directly in the given arrays, output will be handled by the driver code.<br>

Examples<br>

Input: n = 5, nuts[] = {@, %, $, #, ^}, bolts[] = {%, @, #, $ ^}<br>
Output: <br>
# $ % @ ^<br>
# $ % @ ^<br>
Explanation: As per the order # should come first after that $ then % then @ and ^. <br>
Input: n = 9, nuts[] = {^, &, %, @, #, *, $, ?, !}, bolts[] = {?, #, @, %, &, *, $ ,^, !}<br>
Output: <br>
! # $ % & * ? @ ^<br>
! # $ % & * ? @ ^<br>
Explanation: We'll have to match first ! then  # , $,  %,  &,  *,  @,  ^,  ? as per the required ordering.<br>
Expected Time Complexity: O(n(logn))<br>
Expected Auxiliary Space: O(log(n))<br>

Constraints:<br>
1 <= n <= 9<br>
The arrays 'nuts' and 'bolts' can only consist of the following elements: {'@', '#', '$', '%', '^', '&', '?', '*', '!'}.<br>
All the elements of arrays 'nuts' and 'bolts' should be unique.<br>

__Intuition ->Store all the nuts in a set. Also , store all the elements(given) in a temp array. Now , traverse the temp array and check if it is present in the set . If it is present , keep updating the nuts and bolts array.__

```C++
void matchPairs(int n, char nuts[], char bolts[]) {
        // code here
        char temp[] = { '!','#','$','%','&','*','?','@','^' };
        
        unordered_set<char>st;
        
        for(int i=0;i<n;i++){
            st.insert(nuts[i]);
        }
        
        int k = 0;
        
        for(auto &c:temp){
            if(st.find(c)!=st.end()){
                nuts[k]=c;
                bolts[k]=c;
                k++;
            }
        }
        
    }
```
