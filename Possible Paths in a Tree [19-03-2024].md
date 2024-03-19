Given a weighted tree with n nodes and (n-1) edges. You are given q queries. Each query contains a number x. For each query, find the number of paths in which the maximum edge weight is less than or equal to x.<br>

Note: Path from A to B and B to A are considered to be the same.<br>

Example 1:<br>

Input: <br>
n = 3<br>
edges {start, end, weight} = {{1, 2, 1}, {2, 3, 4}}<br>
q = 1<br>
queries[] = {3}<br>
Output: 
1<br>
Explanation:<br>
Query 1: Path from 1 to 2<br>
Example 2:<br>

Input: <br>
n = 7<br>
edges {start, end, weight} = {{1, 2, 3}, {2, 3, 1}, {2, 4, 9}, {3, 6, 7}, {3, 5, 8}, {5, 7, 4}}<br>
q = 3<br>
queries[] = {1, 3, 5}<br>
Output: 
1 3 4<br>
Explanation: <br>
Query 1: Path from 2 to 3<br>
Query 2: Path from 1 to 2, 1 to 3, and 2 to 3<br>
Query 3: Path from 1 to 2, 1 to 3, 2 to 3, and 5 to 7<br>
Your Task:  <br>
You don't need to read input or print anything. Complete the function maximumWeight()which takes integers n, list of edges where each edge is given by {start,end,weight}, an integer q and a list of q queries as input parameters and returns a list of integers denoting the number of possible paths for each query. <br>

Expected Time Complexity: O(nlogn + qlogn)<br>
Expected Auxiliary Space: O(n)<br>

Constraints:<br>
2 ≤ n ≤ 10^4<br>
1 ≤ q ≤ 10^4<br>
1 ≤ edges[i][0], edges[i][1] ≤ n<br>
edges[i][0] != edges[i][1]<br>
0 ≤ edges[i][2] ≤ 10^5<br>
0 ≤ queries[i] ≤ 10^5<br>


__Intuition -> Use concept of Disjoint Sets ( Find by Compression and Union) . Use map to store (weight,size of disjoint sets).__

```C++
int ans;
    vector<int> parent;
vector<int> size;

vector<int> maximumWeight(int n, vector<vector<int>>& edges, int q, vector<int>& queries) {
    ans = 0;

    parent.resize(n + 1);
    size.resize(n + 1, 1);
    for (int i = 0; i <= n; i++) {
        parent[i] = i;
    }
    vector<int> res;
    map<int, int> mp; // asc sorted

    // Sorting the edges based on their weights in ascending order to get our work done.
    sort(edges.begin(), edges.end(), [](const vector<int>& a, const vector<int>& b) {
        return a[2] < b[2];
    });

    for (int i = 0; i < n - 1; i++) {
        // (k,v) - value is the number of path within which mx wt <= k
        mp[edges[i][2]] = Union(edges[i][0], edges[i][1]);
    }

    for (int query : queries) { //q logn
        int maxWeight = 0;
        for (auto& entry : mp) {
            if (entry.first <= query)
                maxWeight = entry.second;
            else
                break;
        }
        res.push_back(maxWeight);
    }
    return res;
}

int find(int x) {
    if (x == parent[x])
        return x;

    return parent[x] = find(parent[x]); // find path compression
}

int Union(int a, int b) {
    int rootA = find(a);
    int rootB = find(b);

    // union by rank - bigger rank always become parent to avoid chaining
    if (size[rootA] < size[rootB]) {
        ans += size[rootA] * size[rootB];  // only change
        parent[rootA] = rootB;
        size[rootB] += size[rootA];
    } else if (size[rootA] > size[rootB]) {
        ans += size[rootA] * size[rootB];
        parent[rootB] = rootA;
        size[rootA] += size[rootB];
    } else {
        ans += size[rootA] * size[rootB];
        parent[rootB] = rootA;
        size[rootA] += size[rootB];
    }

    return ans;
}
```
