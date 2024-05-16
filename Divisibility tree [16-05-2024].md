[Problem Link](https://www.geeksforgeeks.org/problems/divisibility-tree1902/1)<br>
Given a tree with n nodes numbered from 1 to n and n - 1 edges connecting them. The tree is rooted at node 1. Your task is to remove a maximum number of edges from the given tree such that the tree converts into a disjoint union tree and the nodes of connected components left are divisible by 2. If n is odd, then it is allowed to keep exactly one component with an odd number of nodes. <br>

Example 1:<br>

Input: 
n = 10<br>
edges = {{2,1},{3,1},{4,3},{5,2},{6,1},{7,2},{8,6},{9,8},{10,8}}<br>
Output:
2<br>
Explanation:
Take two integers at a time i.e. 2 is connected with 1, 3 is connected with 1,4 is 
connected with 3, 5 is connected with 2 and so on. Fig will understand you better.<br>
Original tree:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/16e551dd-6559-4a6e-967f-5efa91f244b9)<br>

   
After removing edge 1-3 and 1-6. So ans is 2 because all nodes are even.<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/5d7e151c-b680-4e7d-b531-6479d1d88c85)<br>


Example 2:<br>

Input: 
n = 4<br>
edges = {{2,1},{4,2},{1,3}}<br>
Output:
1<br>
Explanation:
Removing the edge 2-1 will convert the tree into disjoint union tree with nodes of connected component left is divisible by 2. <br>
Your Task:
You don't need to read or print anyhting. Your task is to complete the function minimumEdgeRemove() which takes n and edges as input parameter and returns the minimum number of edges which is removed to make the tree disjoint union tree such that the tree converts into disjoint union tree so that nodes of connected component left is divisible by 2.<br>

Expected Time Compelxity: O(n)<br>
Expected Space Comeplxity: O(1)<br>

Constraints:<br>
1 <= n <= 10^5<br>
edges.length == n - 1<br>
1 <= edges[i][0], edges[i][1] <= n<br>

__Intuition ->Use DFS.Go from node 1 to n. For each node , go to its adjacent node (using adjacency list) and find the number of nodes. If the number of nodes is even , increment the ans.__

```C++
int help(vector<int>adj[],vector<int>&vis,int& ans , int node){
        
        vis[node]=1;
        int size = 1;
        
        for(int x:adj[node]){
            if(!vis[x]){
                int temp = help(adj,vis,ans,x);
                size+=temp;
                
                if(temp%2==0){
                    ans++;
                }
            }
        }
        
        return size;
    }
	int minimumEdgeRemove(int n, vector<vector<int>>edges){
	    
	    vector<int>adj[n+1];
	    
	    for(auto x:edges){
	        adj[x[0]].push_back(x[1]);
	        adj[x[1]].push_back(x[0]);
	    }
	        
	        vector<int>vis(n+1,0);
	        int ans=0;
	        
	        for(int i=1;i<=n;i++){
	            if(!vis[i]){
	                help(adj,vis,ans,i);
	            }
	        }
	    return ans;
	}
```
