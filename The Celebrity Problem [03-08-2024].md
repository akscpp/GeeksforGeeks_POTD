[Problem Link](https://www.geeksforgeeks.org/problems/the-celebrity-problem/1)<br>

A celebrity is a person who is known to all but does not know anyone at a party. A party is being organized by some people.  A square matrix mat is used to represent people at the party such that if an element of row i and column j is set to 1 it means ith person knows jth person. You need to return the index of the celebrity in the party, if the celebrity does not exist, return -1.

Note: Follow 0-based indexing.

Examples:
![image](https://github.com/user-attachments/assets/451c0f76-d007-4167-9ead-0c05d55d6f51)


Expected Time Complexity: O(n^2)
Expected Auxiliary Space: O(1)

Constraints:
1 <= mat.size()<= 3000
0 <= mat[i][j]<= 1


__Intuition ->First, find the row which does not contain any 1. Then , find if that column does not contain any 0 (except in the same row).__

```C++
int celebrity(vector<vector<int> >& mat) {
        int n = mat.size();
        int m = mat[0].size();
        int ind=-1;
        for(int i=0;i<n;i++){
            bool flag = true;
            for(int j=0;j<m;j++){
                if(mat[i][j]==1){
                    flag = false;
                }
            }
            
            if(flag==true){
                ind = i;
            }
        }
        
        if(ind==-1) return -1;
        
        for(int i=0;i<m;i++){
            if(i!=ind && mat[i][ind]!=1) return -1;
        }
        
        return ind;
    }
```
