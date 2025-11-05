# Question  

Given an weighted graph with V vertices numbered from 0 to V-1 and E edges, represented by a 2d array edges[][], where edges[i] = [u, v, w] represents a direct edge from node u to v having w edge weight. You are also given a source vertex src.

Your task is to compute the shortest distances from the source to all other vertices. If a vertex is unreachable from the source, its distance should be marked as 108. Additionally, if the graph contains a negative weight cycle, return [-1] to indicate that shortest paths cannot be reliably computed.



##### Examples :

Input: V = 5, edges[][] = [[1, 3, 2], [4, 3, -1], [2, 4, 1], [1, 2, 1], [0, 1, 5]], src = 0

Output: [0, 5, 6, 6, 7]

Explanation: Shortest Paths:
For 0 to 1 minimum distance will be 5. By following path 0 → 1
For 0 to 2 minimum distance will be 6. By following path 0 → 1  → 2
For 0 to 3 minimum distance will be 6. By following path 0 → 1  → 2 → 4 → 3 
For 0 to 4 minimum distance will be 7. By following path 0 → 1  → 2 → 4




### Solve: [https://www.geeksforgeeks.org/problems/distance-from-the-source-bellman-ford-algorithm/1](https://www.geeksforgeeks.org/problems/distance-from-the-source-bellman-ford-algorithm/1)

*** 

# Optimal Solution 

``` java
    public int[] bellmanFord(int V, int[][] edges, int k) {
        // code here
        int res[] = new int[V];
        Arrays.fill(res,(int)1e8);
        res[k] = 0;
        for(int i=1;i<V;++i){
            for(int[] edge:edges){
                int src = edge[0];
                int des = edge[1];
                int dis = edge[2];
                if(res[src]!=(int)1e8 && res[des]>res[src]+dis){
                    res[des] = res[src]+dis;
                }
            }
        }
        for(int edge[]:edges){
            int src = edge[0];
            int des = edge[1];
            int dis = edge[2];
            if(res[src]!=(int)1e8 && res[des]>res[src]+dis){
                return new int[]{-1};
            }
        }
        return res;
    }
```