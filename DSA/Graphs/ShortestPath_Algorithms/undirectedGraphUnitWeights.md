# Question  

You are given an adjacency list, adj of Undirected Graph having unit weight of the edges, find the shortest path from src to all the vertex and if it is unreachable to reach any vertex, then return -1 for that vertex.




##### Examples :

Input: adj[][] = [[1, 3], [0, 2], [1, 6], [0, 4], [3, 5], [4, 6], [2, 5, 7, 8], [6, 8], [7, 6]], src=0

Output: [0, 1, 2, 1, 2, 3, 3, 4, 4]




### Solve: [https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph-having-unit-distance/1](https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph-having-unit-distance/1)

*** 

# Optimal Solution 

``` java
    public int[] shortestPath(ArrayList<ArrayList<Integer>> adj, int src) {
        // code here
        int V = adj.size();
        int res[] = new int[V];
        boolean vis[] = new boolean[V];
        ArrayDeque<Integer> q = new ArrayDeque<>();
        Arrays.fill(res,-1);
        res[src] = 0;
        q.addLast(src);
        int depth = 0;
        while(!q.isEmpty()){
            int len = q.size();
            depth++;
            for(int i=0;i<len;++i){
                int node = q.pollFirst();
                for(int curr: adj.get(node)){
                    if(res[curr]==-1){
                        res[curr] = depth;
                        q.addLast(curr);
                    }
                }   
            }
        }
        return res;
    }
```