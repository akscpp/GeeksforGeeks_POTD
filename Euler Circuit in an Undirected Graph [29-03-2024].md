[Problem Link](https://www.geeksforgeeks.org/problems/euler-circuit-in-a-directed-graph/1)<br>
Eulerian Path is a path in a graph that visits every edge exactly once. Eulerian Circuit is an Eulerian Path that starts and ends on the same vertex. Given the number of vertices v and adjacency list adj denoting the graph. Find that there exists the Euler circuit or not. Return 1 if there exist  alteast one eulerian path else 0.<br>

Example 1:<br>

Input: 
v = 4 <br>
edges[] = {{0, 1}, <br>
           {0, 2}, <br>
           {1, 3}, <br>
           {2, 3}}<br>

Output: 
1<br>
Explanation: corresponding adjacency list will be {{1, 2},{0, 3},{0, 3},{1, 2}}<br>
One of the Eularian circuit 
starting from vertex 0 is as follows:<br>
0->1->3->2->0<br>
Example 2:<br>

Input: 
v = 3<br>
edges[] = {{0, 1}, <br>
         {0, 2}}<br>
         

Output: 
0<br>
Explanation: corresponding adjacency list will be {{1, 2}}<br>
No Eulerian path is found.<br>
Your Task:<br>
You don't need to read or print anything. Your task is to complete the function isEularCircuitExist() which takes v and adjacency list adj[] as input parameter and returns boolean value 1 if Eular circuit exists otherwise returns 0.<br>

Expected Time Complexity: O(v + e)<br>
Expected Space Complexity: O(v)<br>

Constraints:<br>
1 <= v <= 10^5<br>
1 <= edges <= 2*10^5<br>

__Intuition -> Use Degree Rule - If in a graph , all the nodes are of even indegree then the graph is Euler graph and hence it contains a euler circuit. In this , calculate degree of all the nodes. Then check of the condition.__

```C++
	bool isEularCircuitExist(int v, vector<int>adj[]){
	    // Code here
	    vector<int>indegree(v,0);
	    
	    for(int i=0;i<v;i++){
	        for(auto it:adj[i]){
	            indegree[it]++;
	        }
	    }
	    
	    for(int i=0;i<v;i++){
	        if(indegree[i]%2!=0){
	            return 0;
	        }
	    }
	    return 1;
	
	}
```
