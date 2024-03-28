[Problem Link](https://www.geeksforgeeks.org/problems/city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/1)<br>
There are n cities labeled from 0 to n-1 with m edges connecting them. Given the array edges where edges[i] = [from i , to i ,weight i]  represents a bidirectional and weighted edge between cities from i and 
to i, and given the integer distanceThreshold. You need to find out a city with the smallest number of cities that are reachable through some path and whose distance is at most Threshold Distance. If there are multiple such cities, our answer will be the city with the greatest label.<br>

Note: The distance of a path connecting cities i and j is equal to the sum of the edge's weights along that path.<br>

Example 1:<br>

Input:<br>
n = 4, m = 4<br>
edges = [[0, 1, 3],<br>
         [1, 2, 1], <br>
         [1, 3, 4], <br> 
         [2, 3, 1]]<br>
distanceThreshold = 4<br>
Output:
3<br>
Explaination:

The neighboring cities at a distanceThreshold = 4 for each city are:<br>
City 0 -> [City 1, City 2] <br>
City 1 -> [City 0, City 2, City 3] <br>
City 2 -> [City 0, City 1, City 3] <br>
City 3 -> [City 1, City 2] <br>
Cities 0 and 3 have 2 neighboring cities at a distanceThreshold = 4, but we have to return city 3 since it has the greatest number.<br>
Example 2:<br>

Input: <br>
n = 5, m = 6<br>
edges = [[0, 1, 2],<br>
         [0, 4, 8],<br>
         [1, 2, 3], <br>
         [1, 4, 2], <br>
         [2, 3, 1],<br>
         [3, 4, 1]]<br>
distanceThreshold = 2.<br>
Output:
0<br>
Explaination:<br>

The neighboring cities at a distanceThreshold = 2 for each city are:<br>
City 0 -> [City 1] <br>
City 1 -> [City 0, City 4] <br>
City 2 -> [City 3, City 4] <br>
City 3 -> [City 2, City 4]<br>
City 4 -> [City 1, City 2, City 3] <br>
The city 0 has 1 neighboring city at a distanceThreshold = 2.<br>
Your Task:<br>
You don't need to read input or print anything. Your task is to complete the function findCity( ) which takes a number of nodes n, total number of edges m and vector of edges and distanceThreshold. and return the city with the smallest number of cities that are reachable through some path and whose distance is at most Threshold Distance. If there are multiple such cities, return the city with the greatest label.<br>

Expected Time Complexity: O(n^2 + length(edges)*nlog(n) )<br>
Expected Auxiliary Space:  O(n^3)<br>

Constraints:<br>
1  ≤  n ≤  100<br>
1 <= m <= n*(n-1)/2<br>
length(edges[i]) == 3<br>
0 <= from i < to i < n<br>
1 <= weighti distanceThreshold <= 10^4<br>
All pairs (from i, to i) are distinct<br>

__Intuition -> Use Floyd Warshall algorithm . For storing count , start with cityCount = n then keep reducing the answer space. Why? Because the question says to return city with greatest label.__

```C++
int findCity(int n, int m, vector<vector<int>>& edges, int distanceThreshold) {
        
        /*First create a distance array - which will be an array which will contain
        shortest distance from any point to every other point constructed using 
        floyd warshall algorith
        */
        
        vector<vector<int>>dist(n,vector<int>(n,1e9));
        
        // Construct this matrix acc. to the given edges
        for(auto it:edges){
            dist[it[0]][it[1]]=it[2];
            dist[it[1]][it[0]]=it[2];
        }
        
        //For same index , distance is 0 -> dist[0][0]=0
        for(int i=0;i<n;i++){
            dist[i][i]=0;
        }
        
        //Floyd warshall
        for(int k=0;k<n;k++){
            for(int i=0;i<n;i++){
                for(int j=0;j<n;j++){
                    dist[i][j]=min(dist[i][k]+dist[k][j],dist[i][j]);
                }
            }
        }
        
        int cityCnt=n;
        int cityNo=-1;
        
        for(int city=0;city<n;city++){
            int cnt=0; //count for each city
            for(int adjCity=0;adjCity<n;adjCity++){
                if(dist[city][adjCity]<=distanceThreshold){
                    cnt++;
                }
            }
            if(cnt<=cityCnt){
                cityCnt=cnt;
                cityNo = city;
            }
        }
        return cityNo;
    }
```

