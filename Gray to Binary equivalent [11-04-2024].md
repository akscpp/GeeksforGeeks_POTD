[Problem Link](https://www.geeksforgeeks.org/problems/gray-to-binary-equivalent-1587115620/1)<br>
Given an integer number n, which is a decimal representation of Gray Code. Find the binary equivalent of the Gray Code & return the decimal representation of the binary equivalent.<br>

 

Note: Please visit [here](https://docs.google.com/document/d/1JvuMcN8XXUP_bOiZmVvbNskWu4K2ieA0aoCJWAEexEM/edit) to learn How Gray Code is generated.<br>

Example 1:<br>

Input: 
n = 4<br>
Output: 
7<br>
Explanation:<br>
Given 4, its gray code =  110.<br>
Binary equivalent of the gray code 110 is 100.<br>
Return 7 representing gray code 100.<br>
Example 2:<br>

Input: 
n = 15<br>
Output: 
10<br>
Explanation:<br>
Given 15 representing gray code 1000.<br>
Binary equivalent of gray code 1000 is 1111.<br>
Return 10 representing gray code 1111
ie binary 1010.<br>
Your Task: <br>
You don't need to read input or print anything. Your task is to complete the function grayToBinary() which accepts an integer n as an input parameter and returns decimal representation of the binary equivalent of the given gray code.<br>

Expected Time Complexity: O(log (n)).<br>
Expected Auxiliary Space: O(1).<br>

Constraints:<br>
0 <= n <= 10^8<br>

__Intuition-> Convert the given decimal number to binary. Then convert that binary to gray code . At last ,convert that gray code to decimal.__

```C++
int grayToBinary(int n)
    {
        
        // Your code here
        vector<int>temp;
        
        //Binary conversion
        while(n){
            if(n & 1){
                temp.push_back(1);
            }else {
                temp.push_back(0);
            }
            
            n=n>>1;
        }
        
        reverse(temp.begin(),temp.end());
        
       //Gray code conversion
        for(int i=1;i<temp.size();i++){
            temp[i]=temp[i-1]^temp[i];
        }
        
        
        int j=0;
        int ans=0;
        //Gray code to decimal conversion
        for(int i=temp.size()-1;i>=0;i--){
            ans+= (1<<j)*temp[i];
            j++;
        }
        return ans;
        
    }
```
