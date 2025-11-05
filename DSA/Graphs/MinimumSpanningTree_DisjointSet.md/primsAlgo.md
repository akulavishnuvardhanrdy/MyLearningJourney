# Question  

Given a weighted, undirected, and connected graph with V vertices and E edges, your task is to find the sum of the weights of the edges in the Minimum Spanning Tree (MST) of the graph. The graph is provided as a list of edges, where each edge is represented as [u, v, w], indicating an edge between vertex u and vertex v with edge weight w.



##### Examples :

Input: V = 3, E = 3, Edges = [[0, 1, 5], [1, 2, 3], [0, 2, 1]]
 
Output: 4




### Solve: [https://www.geeksforgeeks.org/problems/minimum-spanning-tree/1](https://www.geeksforgeeks.org/problems/minimum-spanning-tree/1)

*** 

# Optimal Solution 

``` java
    public int spanningTree(int V, int[][] edges) {
        // code here
        List<List<Edge>> adj = new ArrayList<>();
        boolean vis[] = new boolean[V];
        for(int i=0;i<V;++i)
            adj.add(new ArrayList<>());
        for(int edge[]:edges){
            adj.get(edge[0]).add(new Edge(edge[2],edge[1],edge[0]));
            adj.get(edge[1]).add(new Edge(edge[2],edge[0],edge[1]));
        }
        int sum = 0;
        List<Edge> mst = new ArrayList<>();
        PriorityQueue<Edge> pq = new PriorityQueue<>(
            (a,b)->a.wt-b.wt    
        );
        pq.add(new Edge(0,0,-1));
        while(!pq.isEmpty()){
            Edge e = pq.poll();
            if(vis[e.node])
                continue;
            vis[e.node] = true;
            sum+=e.wt;
            if(e.parent!=-1)    
                mst.add(new Edge(e.wt,e.node,e.parent));
            for(Edge curr:adj.get(e.node)){
                if(!vis[curr.node]){
                    pq.add(new Edge(curr.wt,curr.node,e.node));
                }
            }
        }
        return sum;
    }
    static class Edge{
        int wt;
        int node;
        int parent;
        Edge(int wt,int node,int parent){
            this.wt = wt;
            this.node = node;
            this.parent = parent;
        }
        public String toString(){
            return parent+"->"+wt+"->"+node;
        }
    }
```