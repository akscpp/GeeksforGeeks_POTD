[Problem Link](https://www.geeksforgeeks.org/problems/compare-two-fractions4438/1)<br>

You are given a string str containing two fractions a/b and c/d, compare them and return the greater. If they are equal, then return "equal".<br>

Note: The string str contains "a/b, c/d"(fractions are separated by comma(,) & space( )). <br>

Examples<br>



Input: str = "5/6, 11/45"<br>
Output: 5/6<br>
Explanation: 5/6=0.8333 and 11/45=0.2444, So 5/6 is greater fraction.<br>
Input: str = "8/1, 8/1"<br>
Output: equal<br>
Explanation: We can see that both the fractions are same, so we'll return a string "equal".<br>
Input: str = "10/17, 9/10"<br>
Output: 9/10<br>
Explanation: 10/17 = 0.588 & 9/10 = 0.9, so the greater fraction is "9/10".<br>
Expected Time Complexity: O(len|str|)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:
0<=a,c<=10^3<br>
1<=b,d<=10^3<br>

__Intuition ->Use REGEX expression to find the numerators and denominators of both fractions.__

```C++
string compareFrac(string str) {
        int a=0,b=0,c=0,d=0;
        
        regex re("([0-9]+)\\/([0-9]+), ([0-9]+)\\/([0-9]+)",
        regex_constants :: ECMAScript);
        
        smatch sm;
        
        if(regex_search(str,sm,re)){
            a = stoi(sm[1]);
            b = stoi(sm[2]);
            
            c = stoi(sm[3]);
            d = stoi(sm[4]);
        }
        
        string ans = "";
        
        if(a*d > b*c){
            ans+=to_string(a);
            ans+="/";
            ans+=to_string(b);
        }else if(a*d < b*c){
            ans+= to_string(c);
            ans+="/";
            ans+= to_string(d);
        }else {
            ans = "equal";
        }
        
        return ans;
    }
```
