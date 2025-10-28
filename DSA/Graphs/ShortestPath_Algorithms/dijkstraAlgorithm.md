# Question  

Given an undirected, weighted graph with V vertices numbered from 0 to V-1 and E edges, represented by 2d array edges[][], where edges[i]=[u, v, w] represents the edge between the nodes u and v having w edge weight.
You have to find the shortest distance of all the vertices from the source vertex src, and return an array of integers where the ith element denotes the shortest distance between ith node and source vertex src.

Note: The Graph is connected and doesn't contain any negative weight edge.



##### Examples :

Input: V = 3, edges[][] = [[0, 1, 1], [1, 2, 3], [0, 2, 6]], src = 2

Output: [4, 3, 0]

Explanation:

Shortest Paths:
For 2 to 0 minimum distance will be 4. By following path 2 -> 1 -> 0
For 2 to 1 minimum distance will be 3. By following path 2 -> 1
For 2 to 2 minimum distance will be 0. By following path 2 -> 2




### Solve: [https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1](https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)

*** 

# Optimal Solution 

``` java
    public static int[] dijkstra(int V, int[][] edges, int src) {
        // code here
        List<List<Edge>> adj = new ArrayList<>();
        int res[] = new int[V];
        Arrays.fill(res,Integer.MAX_VALUE);
        boolean vis[] = new boolean[V];
        PriorityQueue<Pair> pq = new PriorityQueue<>(
            (a,b)-> a.dis==b.dis?a.ver-b.ver:a.dis-b.dis    
        );
        res[src] = 0;
        for(int i=0;i<V;++i){
            adj.add(new ArrayList<>());
        }
        for(int[] e:edges){
            adj.get(e[0]).add(new Edge(e[1],e[2]));
            adj.get(e[1]).add(new Edge(e[0],e[2]));
        }
        pq.add(new Pair(0,src));
        while(!pq.isEmpty()){
            Pair node = pq.poll();
            if(vis[node.ver])
                continue;
            vis[node.ver] = true;
            for(Edge curr:adj.get(node.ver)){
                int newDis = node.dis+curr.wi;
                if(newDis<res[curr.to]){
                    res[curr.to] = newDis;
                    pq.add(new Pair(newDis,curr.to));
                }
            }
        }
        return res;
    }
    
    static class Pair{
        int dis;
        int ver;
        Pair(int dis,int ver){
            this.dis = dis;
            this.ver = ver;
        }
    }
    
    static class Edge{
        int to;
        int wi;
        Edge(int to,int wi){
            this.to = to;
            this.wi = wi;
        }
    }
```