# Question  

There is an undirected graph with n nodes, where each node is numbered between 0 and n - 1. You are given a 2D array graph, where graph[u] is an array of nodes that node u is adjacent to. More formally, for each v in graph[u], there is an undirected edge between node u and node v. The graph has the following properties:

There are no self-edges (graph[u] does not contain u).
There are no parallel edges (graph[u] does not contain duplicate values).
If v is in graph[u], then u is in graph[v] (the graph is undirected).
The graph may not be connected, meaning there may be two nodes u and v such that there is no path between them.
A graph is bipartite if the nodes can be partitioned into two independent sets A and B such that every edge in the graph connects a node in set A and a node in set B.

Return true if and only if it is bipartite.



##### Examples :

Input: graph = [[1,2,3],[0,2],[0,1,3],[0,2]]

Output: false

Explanation: There is no way to partition the nodes into two independent sets such that every edge connects a node in one and a node in the other.




### Solve: [https://leetcode.com/problems/is-graph-bipartite/](https://leetcode.com/problems/is-graph-bipartite/)

*** 

# Optimal Solution 

``` java
    public boolean isBipartite(int[][] graph) {
        int[] color = new int[graph.length];
        Arrays.fill(color,-1);
        boolean vis[] = new boolean[graph.length];
        for(int i=0;i<graph.length;++i){
            if(!vis[i]){
                color[i] = 0;
                if(!dfs(graph,color,vis,i,0))
                    return false;
            }
        }
        return true;
    }
    boolean dfs(int[][] graph,int[] color,boolean vis[],int node,int c){   
        vis[node] = true;
        for(int adj:graph[node]){
            if(!vis[adj]){
                color[adj] = c==0?1:0;
                vis[adj] = true;
                if(!dfs(graph,color,vis,adj,color[adj]))
                    return false;
            }
            else if(color[adj]==c)
                return false;
        }
        return true;   
    }
```