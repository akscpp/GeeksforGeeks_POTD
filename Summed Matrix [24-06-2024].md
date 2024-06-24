[Problem Link](https://www.geeksforgeeks.org/problems/summed-matrix5834/1)<br>
A matrix is constructed of size n*n and given an integer ‘q’. The value at every cell of the matrix is given as, M(i,j) = i+j, where ‘M(i,j)' is the value of a cell, ‘i’ is the row number, and ‘j’ is the column number. Return the number of cells having value ‘q’.<br>

Note: Assume, the array is in 1-based indexing.<br>

Examples:<br>

Input: n = 4, q = 7<br>
Output: 2<br>
Explanation: Matrix becomes<br>
2 3 4 5 <br>
3 4 5 6 <br>
4 5 6 7<br>
5 6 7 8<br>
The count of 7 is 2.<br>
Input: n = 5, q = 4<br>
Output: 3<br>
Explanation: Matrix becomes<br>
2 3 4 5 6 <br>
3 4 5 6 7 <br>
4 5 6 7 8 <br>
5 6 7 8 9 <br>
6 7 8 9 10 <br>
The count of 4 is 3.<br>
Expected Time Complexity: O(1)<br>
Expected Auxiliary Space: O(1)<br>

Constraints:<br>
1 ≤ n,q ≤ 10^18<br>

__Intuition ->The problem involves finding the number of cells in an n×n matrix where each cell value M(i,j) equals i+j, given a specific value q. To achieve this efficiently, without iterating through the matrix, we leverage the mathematical constraints of the indices. We identify that the cells with value q lie on the diagonal where i+j=q. By considering the minimum and maximum bounds of i and j within the matrix dimensions, we can determine the count of valid cells that meet the condition i+j=q in constant time O(1). This approach ensures an optimal solution even for very large matrix sizes up to 10^18.__

```C++
long long sumMatrix(long long n, long long q) {
        // code here.`
        if(q>2*n || q<2) return 0;
        
        else if(n>=q){
            return q-1;
        }else{
            long long diff = q-n;
            return n-(diff-1);
        }
    }
```
