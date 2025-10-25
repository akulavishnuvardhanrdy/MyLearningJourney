# Question  

Given an undirected graph with V vertices and E edges, represented as a 2D vector edges[][], where each entry edges[i] = [u, v] denotes an edge between vertices u and v, determine whether the graph contains a cycle or not.

Note: The graph can have multiple component.



##### Examples :

Input: V = 4, E = 4, edges[][] = [[0, 1], [0, 2], [1, 2], [2, 3]]

Output: true

Explanation:  
1 -> 2 -> 0 -> 1 is a cycle.



### Solve: [https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1](https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

*** 

# Optimal Solution 

``` java
    public boolean isCycle(int V, int[][] edges) {
        // Code here
        List<List<Integer>> ls = new ArrayList<>();
        boolean vis[] = new boolean[V];
        for(int i=0;i<V;++i){
            ls.add(new ArrayList<>());
        }
        for(int i=0;i<edges.length;++i){
            int temp[] = edges[i];
            ls.get(temp[0]).add(temp[1]);
            ls.get(temp[1]).add(temp[0]);
        }
        for(int i=0;i<V;++i){
            if(!vis[i]){
                if(isCycle(ls,vis,i)) return true;
            }
        }
        return false;
    }
    boolean isCycle(List<List<Integer>> adj,boolean vis[],int src){
        vis[src] = true;
        ArrayDeque<int []> q = new ArrayDeque<>();
        q.add(new int[]{src,-1});
        while(!q.isEmpty()){
            int node = q.peekFirst()[0];
            int parent = q.pollFirst()[1];
            List<Integer> ls = adj.get(node);
            for(int curr:ls){
                if(!vis[curr]){
                    q.addLast(new int[]{curr,node});
                    vis[curr] = true;
                }
                else if(curr!=parent){
                    return true;
                }
            }
        }
        return false;
    }
```