# Question  

Given a Directed Acyclic Graph (DAG) of V (0 to V-1) vertices and E edges represented as a 2D list of edges[][], where each entry edges[i] = [u, v] denotes a directed edge u -> v. Return the topological sort for the given graph.

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge u -> v, vertex u comes before v in the ordering.
Note: As there are multiple Topological orders possible, you may return any of them. If your returned Topological sort is correct then the output will be true else false.



##### Examples :

Input: V = 4, E = 3, edges[][] = [[3, 0], [1, 0], [2, 0]]

Output: true

Explanation: The output true denotes that the order is valid. Few valid Topological orders for the given graph are:
[3, 2, 1, 0]
[1, 2, 3, 0]
[2, 3, 1, 0]




### Solve: [https://www.geeksforgeeks.org/problems/topological-sort/1](https://www.geeksforgeeks.org/problems/topological-sort/1)

*** 

# Optimal Solution 

``` java
    public static ArrayList<Integer> topoSort(int V, int[][] edges) {
        // code here
        List<List<Integer>> adj = new ArrayList<>();
        for(int i=0;i<V;++i)
            adj.add(new ArrayList<>());
        for(int i=0;i<edges.length;++i){
            adj.get(edges[i][0]).add(edges[i][1]);
        }
        ArrayDeque<Integer> st = new ArrayDeque<>();
        boolean vis[] = new boolean[V];
        for(int i=0;i<V;++i){
            if(!vis[i])
                dfs(adj,vis,st,i);
        }
        ArrayList<Integer> res = new ArrayList<>(st);
        Collections.reverse(res);
        return res;
    }
    static void dfs(List<List<Integer>> adj,boolean vis[],ArrayDeque<Integer> st,int node){
        vis[node] = true;
        for(int curr:adj.get(node)){
            if(!vis[curr]){
                dfs(adj,vis,st,curr);
            }
        }
        st.addLast(node);
    }
```