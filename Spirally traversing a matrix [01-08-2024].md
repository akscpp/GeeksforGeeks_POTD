[Problem Link](https://www.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1)<br>

You are given a rectangular matrix, and your task is to return an array while traversing the matrix in spiral form.<br>

![image](https://github.com/user-attachments/assets/23e8492d-deb0-4af2-9b0e-3ef3387fbf9a)
![image](https://github.com/user-attachments/assets/b719a79c-4080-4d0b-8ce8-47a7a2d97514)

Expected Time Complexity: O(n^2)<br>
Expected Auxiliary Space: O(n^2)<br>

Constraints:<br>
1 <= matrix.size(), matrix[0].size() <= 100<br>
0 <= matrix[i][j]<= 100<br>

__Intuition ->Use 4 pointers to traverse the matrix like you are peeling an onion -> layer by layer.__

```C++
vector<int> spirallyTraverse(vector<vector<int> > a) 
    {
        // code here 
        int n = a.size();
        int m = a[0].size();
        vector<int>v;
        int top=0,right=m-1,bottom=n-1,left=0;
        
        while(top<=bottom && left<=right){
            for(int i=left;i<=right;i++){
            v.push_back(a[top][i]);
        }
        top++;
        for(int i=top;i<=bottom;i++){
            v.push_back(a[i][right]);
        }
        right--;
        if(top<=bottom){
            for(int i=right;i>=left;i--){
            v.push_back(a[bottom][i]);
        }
        bottom--;
        }
        if(left<=right){
        for(int i=bottom;i>=top;i--){
            v.push_back(a[i][left]);
        } 
        left++;
        }
    
        }
            
        return v;
    }
```

