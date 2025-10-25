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
                if(isCycle(ls,vis,i,-1)) return true;
            }
        }
        return false;
    }
    boolean isCycle(List<List<Integer>> adj,boolean vis[],int src,int parent){
        vis[src] = true;
        List<Integer> ls = adj.get(src);
        for(int curr:ls){
            if(!vis[curr]){
                if(isCycle(adj,vis,curr,src)) return true;
            }
            else if(curr!=parent){
                return true;
            }
        }
        return false;
    }
```