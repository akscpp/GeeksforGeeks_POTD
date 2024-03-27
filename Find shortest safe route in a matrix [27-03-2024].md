[Problem Link](https://www.geeksforgeeks.org/problems/find-shortest-safe-route-in-a-matrix/1)<br>

Given a matrix mat[][] with r rows and c columns, where some cells are landmines (marked as 0) and others are safe to traverse. Your task is to find the shortest safe route from any cell in the leftmost column to any cell in the rightmost column of the mat. You cannot move diagonally, and you must avoid both the landmines and their adjacent cells (up, down, left, right), as they are also unsafe.<br>

Example 1:<br>

Input:<br>
mat = [1, 0, 1, 1, 1],<br>
      [1, 1, 1, 1, 1],<br>
      [1, 1, 1, 1, 1],<br>
      [1, 1, 1, 0, 1],<br>
      [1, 1, 1, 1, 0]<br>
Output: 
6<br>
Explanation: <br>
We can see that length of shortest
safe route is 6<br>
[1 0 1 1 1]<br>
[1 1 1 1 1] <br>
[1 1 1 1 1]<br>
[1 1 1 0 1] <br>
[1 1 1 1 0]<br>
Example 2:<br>

Input:<br>
mat = [1, 1, 1, 1, 1],<br>
      [1, 1, 0, 1, 1],<br>
      [1, 1, 1, 1, 1]<br>
Output: 
-1<br>
Explanation: There is no possible path from
first column to last column.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function findShortestPath() which takes the matrix as an input parameter and returns an integer denoting the shortest safe path from any cell in the leftmost column to any cell in the rightmost column of mat. If there is no possible path, return -1. <br>

Expected Time Complexity: O(r * c)<br>
Expected Auxiliary Space: O(r * c)<br>

Constraints:<br>
1 <= r, c <= 10^3<br>
0 <= mat[][] <= 1<br>

__Intuition -> Use a queue to store all the cell containing 0. Then use this queue to mark all the adjacent cells as 0 . Now , use another queue to store the row , col ,  distance of 1 in the first column. Now , take them out  one by one and move in all the 4 direction while checking for the validity. If the new cell is valid , store it while doing distance+1. When you reach last column , update answer.__

```C++
void findist(vector<vector<int>> &mat,int dx[],int dy[],int r,int c,int &mindist)
    {
        queue<pair<int,pair<int,int>>>q;
        for(int i=0;i<r;i++)
        {
           if(mat[i][0]==1)
            {
                q.push({i,{0,1}});
            }
        }
           while(!q.empty())
           {
               int i=q.front().first;
               int j=q.front().second.first;
               int dist=q.front().second.second;
               q.pop();
               if(j==c-1)
               {
                   mindist=min(dist,mindist);
                //   cout<<dist<<endl;
               }
               for(int k=0;k<4;k++)
                {
                    int nr=i+dx[k];
                    int nc=j+dy[k];
                               
                    if(nr>=0 && nc>=0 && nr<r && nc<c && mat[nr][nc]!=0)
                    {
                        q.push({nr,{nc,dist+1}});
                        mat[nr][nc]=0;
                    }
                }
           }    
    }
    
    
    int findShortestPath(vector<vector<int>> &mat)
    {
       // code here
       int r=mat.size();
       int c=mat[0].size();
       int dx[]={0,1,0,-1};
       int dy[]={-1,0,1,0};
       queue<pair<int,int>>q;
       
       for(int i=0;i<r;i++)
       {
           for(int j=0;j<c;j++)
           {
               if(mat[i][j]==0)
               {
                   q.push({i,j});
               } 
           }
       }
       
       while(!q.empty())
       {
           int i=q.front().first;
           int j=q.front().second;
           q.pop();
           for(int k=0;k<4;k++)
            {
                int nr=i+dx[k];
                int nc=j+dy[k];
                           
                if(nr>=0 && nc>=0 && nr<r && nc<c)
                {
                    mat[nr][nc]=0;
                }
            }
       }   
       int mindist=INT_MAX;
       findist(mat,dx,dy,r,c,mindist);
       return mindist=mindist==INT_MAX?-1:mindist;
    }
```
