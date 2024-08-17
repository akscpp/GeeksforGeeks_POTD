[Problem Link](https://www.geeksforgeeks.org/problems/additive-sequence/1)<br>

Given a string n, your task is to find whether it contains an additive sequence or not. A string n contains an additive sequence if its digits can make a sequence of numbers in which every number is addition of previous two numbers. You are required to complete the function which returns true if the string is a valid sequence else returns false. For better understanding check the examples.<br>

Note: A valid string should contain at least three digit to make one additive sequence. <br>




Example 1:<br>

Input:  
n = "1235813"<br>
Output: 
1<br>
Explanation: 
The given string can be splited into a series of numbers  <br>
where each number is the sum of the previous two numbers: <br>
1 + 2 = 3, 2 + 3 = 5, 3 + 5 = 8, and 5 + 8 = 13. Hence, the output would be 1 (true).<br>
Example 2:

Input:  
n = "11235815"<br>
Output: 
0<br>
Explanation: <br>
We can start with the first two digits: "11".<br>
First number: 1, Second number: 1, Sum: 1 + 1 = 2<br>
Now, we have "2" as the next number.<br>
First number: 1, Second number: 2, Sum: 1 + 2 = 3<br>
Now, we have "3" as the next number.<br>
First number: 2, Second number: 3, Sum: 2 + 3 = 5<br>
Now, we have "5" as the next number.<br>
First number: 3, Second number: 5, Sum: 3 + 5 = 8<br>
Now, we have "8" as the next number.<br>
First number: 5, Second number: 8, Sum: 5 + 8 = 13<br>
At this point, there is no "13" present in the remaining digits "815". Hence, the output would be 0 (or false).<br>
User Task: <br>
Your task is to complete the function isAdditiveSequence() which takes a single string as input n and returns a boolean value indicating whether the given string contains an additive sequence or not. You need not take any input or print anything.<br>

Expected Time Complexity: O(n^3).<br>
Expected Auxiliary Space: O(n).<br>

Constraints:<br>
3 <= length( n ) <= 200<br>
1 <= digits of string <= 9<br>


__Intuition -> Use nested loops to get first substring and second substring. Use a function to add these strings as if they are numbers. Check if the added string is equal to the third substring. READ COMMENTS FOR MORE CLARIFICATION.__

```C++
string addStrings(string num1,string num2){  //Adding two strings as if they are numbers
        reverse(num1.begin(),num1.end());
        reverse(num2.begin(),num2.end());
        
        string res="";
        int i=0;
        int carry=0;
        
        while(i<min(num1.length(),num2.length())){          //Adding strings to a common length
            int x = carry;
            x+=num1[i]-'0';
            x+=num2[i]-'0';
            carry=x/10;
            x=x%10;
            res=res+to_string(x);
            i++;
        }
        
        while(i<num1.length()){         //If string1 length is bigger
            int x = carry;
            x+=num1[i]-'0';
            // x+=num2[i]-'0';
            carry=x/10;
            x=x%10;
            res=res+to_string(x);
            i++;
        }
        while(i<num2.length()){         //If string 2 length is bigger 
            int x = carry;      
            // x+=num1[i]-'0';
            x+=num2[i]-'0';
            carry=x/10;
            x=x%10;
            res=res+to_string(x);
            i++;
        }
        
        while(carry){                   //Adding carry left 
            int x = carry;
            carry=carry/10;
            x=x%10;
            res=res+to_string(x);
        }
        reverse(res.begin(),res.end());         //reversing the res to get answer
        return res;
    }
    bool isAdditiveSequence(string num) {
        // Your code here
        int n=num.length();
        if(n<3) return false;
        
        for(int i=1;i<=n/2;i++){
            for(int j = 1; max(i,j)<=n-i-j;j++){
                string first = num.substr(0,i);
                string second = num.substr(i,j);
                
                if(first.length()>1 && first[i]=='0'){  //Check for leading 0s in first string
                    break;
                }
                if(second.length()>1 && second[i]=='0'){   //Check for leading 0s in second string
                    break;
                }
                
                int start=i+j; //Third string will start from i+j
                
                string sum;
                
                while(start<n){
                    sum=addStrings(first,second);
                    
                    if(start+sum.length()>n || sum!=num.substr(start,sum.length())){ 
                    /*Check if there is not enough string left to make sunstring of length sum.length 
                    OR check if the third substring is not equal to sum
                    */
                        break;
                    }
                    
                    first=second;
                    second=sum;
                    start+=sum.length();
                }
                if(start==n){
                    return true;
                }
            }
        }
        return false;
        
    }
```
