# Question  

Given a Directed Acyclic Graph of V vertices from 0 to n-1 and a 2D Integer array(or vector) edges[ ][ ] of length E, where there is a directed edge from edge[i][0] to edge[i][1] with a distance of edge[i][2] for all i.

Find the shortest path from src(0) vertex to all the vertices and if it is impossible to reach any vertex, then return -1 for that vertex.




##### Examples :

Input: V = 4, E = 2, edges = [[0,1,2], [0,2,1]]

Output: [0, 2, 1, -1]

Explanation: Shortest path from 0 to 1 is 0->1 with edge weight 2. Shortest path from 0 to 2 is 0->2 with edge weight 1. There is no way we can reach 3, so it's -1 for 3.




### Solve: [https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph/1](https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph/1)

*** 

# Optimal Solution 

``` java
    public int[] shortestPath(int V, int E, int[][] edges) {
        // Code here
        ArrayList<ArrayList<int[]>> adj = new ArrayList<>();
        boolean vis[] = new boolean[V];
        ArrayDeque<Integer> st = new ArrayDeque<>();
        int res[] = new int[V];
        Arrays.fill(res,-1);
        for(int i=0;i<V;++i){
            adj.add(new ArrayList<>());
        }
        for(int i=0;i<edges.length;++i){
            adj.get(edges[i][0]).add(new int[]{edges[i][1],edges[i][2]});
        }
        for(int i=0;i<V;++i){
            if(!vis[i]){
                dfs(adj,vis,st,i);
            }
        }
        res[0] = 0;
        while(!st.isEmpty()){
            if(st.peekLast()==0)
                break;
            else
                st.pollLast();
        }
        while(!st.isEmpty()){
            int node = st.pollLast();
            for(int[] curr:adj.get(node)){
                if(res[curr[0]]==-1){
                    res[curr[0]] = res[node]+curr[1];
                }
                else{
                    res[curr[0]] = Math.min(res[node]+curr[1],res[curr[0]]);
                }
                
            }
        }
        return res;
    }
    void dfs(ArrayList<ArrayList<int[]>> adj,boolean vis[],ArrayDeque<Integer> st,int node){
        vis[node] = true;
        for(int[] curr:adj.get(node)){
            if(!vis[curr[0]]){
                dfs(adj,vis,st,curr[0]);
            }
        }
        st.addLast(node);
    }
```