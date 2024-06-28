[Problem Link](https://www.geeksforgeeks.org/problems/the-palindrome-pattern3900/1)<br>

Given a two-dimensional integer array arr of dimensions n x n, consisting solely of zeros and ones, identify the row or column (using 0-based indexing) where all elements form a palindrome. If multiple palindromes are identified, prioritize the palindromes found in rows over those in columns. Within rows or columns, the palindrome with the smaller index takes precedence. The result should be represented by the index followed by either 'R' or 'C', indicating whether the palindrome was located in a row or column. The output should be space-separated. If no palindrome is found, return the string -1.<br>

Examples:<br>

Input: <br>
arr[][] =  [[1, 0, 0], <br>
           [0, 1, 0],<br>
           [1, 1, 0]]<br>
Output: 1 R<br>
Explanation: In the first test case, 0-1-0 is a palindrome
occuring in a row having index 1.<br>
Input: <br>
arr[][] =   [[1, 0],<br>
           [1, 0]]<br>
Output: 0 C<br>
Explanation: 1-1 occurs before 0-0 in the 0th column. And there is no palindrome in the two rows.<br>
Expected Time Complexity: O(n^2)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1<= arr.size <= 50<br>
0 <= arr[i][j] <= 1<br>

__Intuition ->Separately check for row and column. Use one loop for traversing row and other for checking the palindrome.__

```C++
bool isPalindrome(vector<int>arr,int s, int e){
        
        while(s<=e){
            if(arr[s]==arr[e]){
                s++;
                e--;
            }else return false;
        }
        
        return true;
    }
    string pattern(vector<vector<int>> &arr) {
        
        int n = arr.size();
        
        //Checking rows
        for(int i=0;i<n;i++){
            int start=0;
            int end = n-1;
            
            bool flag= isPalindrome(arr[i],start,end);
            
            if(flag){
                return to_string(i)+" R";
            }
        }
        
        //Checking columns
        for(int i=0;i<n;i++){
            int start = 0;
            int end = n - 1;
        
            vector<int> column(n);
            for (int j = 0; j < n; j++) {
                column[j] = arr[j][i];
            }
        
            bool flag = isPalindrome(column, start, end);
        
            if (flag) {
                return to_string(i) + " C";
            }
        }
        
        return "-1";
    }
```
