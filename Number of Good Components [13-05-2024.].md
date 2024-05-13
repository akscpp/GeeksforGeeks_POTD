[Problem Link](https://www.geeksforgeeks.org/problems/number-of-good-components--170647/1)<br>
Given an undirected graph with v vertices(numbered from 1 to v) and e edges. Find the number of good components in the graph.<br>
A component of the graph is good if and only if the component is fully connected.<br>
Note: A fully connected component is a subgraph of a given graph such that there's an edge between every pair of vertices in the component, the given graph can be a disconnected graph. <br>

Example 1:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/e0b16ea2-50a9-4c2f-a9f9-d4282522de90)

Input: <br>


e=3 <br>
v=3<br>
edges={{1, 2},{1, 3},{3, 2}}<br>
Output: 
1<br>
Explanation: 
We can see that there is only one component in the graph and in this component there is a edge between any two vertces.<br>
Example 2:<br>
![image](https://github.com/akscpp/GeeksforGeeks_POTD/assets/129672950/f15f54f4-4e21-4889-93ec-18fb84f5c357)

Input:<br>

e=5 <br>
v=7<br>
edges={{1, 2},{7, 2},{3, 5},{3, 4},{4, 5}}<br>
Output: 
2<br>
Explanation: 
We can see that there are 3 components in the graph. For 1-2-7 there is no edge between 1 to 7, so it is not a fully connected component. Rest 2 are individually fully connected component.<br>
Your Task:
You don't need to read input or print anything. Your task is to complete the function findNumberOfGoodComponent(), which takes an integer e and v and edges[][] as input parameters and returns an integer denoting the number of good components.<br>

Expected Time Complexity: O(v+e)<br>
Expected Auxiliary Space: O(depth of the graph)<br>

Constraints:<br>
1 <= edges[i][0], edges[i][1] <= v<br>
1 ≤ v, e ≤ 10^4<br>
All edges are unique<br>

__Intuition ->The findNumberOfGoodComponent function counts the number of "good components" in an undirected graph by iterating over each vertex and performing a BFS from that vertex. It checks if the component forms a complete graph, and if so, increments the count of good components. Finally, it returns the total count of good components found in the graph.__

```C++
bool bfs(vector<int>adj[],int start,vector<int>&vis){
        int num = 0, edges=0;
        
        queue<int>q;
        q.push(start);
        
        vis[start]=1;
        
        while(!q.empty()){
            int node = q.front();
            q.pop();
            
            num++;
            edges+=adj[node].size();
            
            for(auto it:adj[node]){
                if(!vis[it]){
                    q.push(it);
                    vis[it]=1;
                }
            }
        }
        
        return (num*(num-1)==edges);
    }
    int findNumberOfGoodComponent(int e, int v, vector<vector<int>> &edges) {
        vector<int>adj[v+1];
        
        for(int i=0;i<e;i++){
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }
        
        vector<int>vis(v+1,0);
        int ans=0;
        
        for(int i=1;i<=v;i++){
            if(bfs(adj,i,vis)){
                ans++;
            }
        }
        return ans;
    }
```
