# Question  

Given an undirected graph with V vertices numbered from 0 to V-1 and E edges, represented as a 2D array edges[][], where each entry edges[i] = [u, v] denotes an edge between vertices u and v.

Your task is to return a list of all connected components. Each connected component should be represented as a list of its vertices, with all components returned in a collection where each component is listed separately.

Note: You can return the components in any order, driver code will print the components in sorted order.



##### Examples :

Input: V = 5, edges[][] = [[0, 1], [2, 1], [3, 4]]

Output: [[0, 1, 2], [3, 4]]




### Solve: [https://www.geeksforgeeks.org/problems/connected-components-in-an-undirected-graph/1](https://www.geeksforgeeks.org/problems/connected-components-in-an-undirected-graph/1)

*** 

# Optimal Solution 

``` java
    public ArrayList<ArrayList<Integer>> getComponents(int V, int[][] edges) {
        // code here
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for(int i=0;i<V;++i){
            adj.add(new ArrayList<>());
        }
        for(int i=0;i<edges.length;++i){
            int pnt1 = edges[i][0];
            int pnt2 = edges[i][1];
            adj.get(pnt1).add(pnt2);
            adj.get(pnt2).add(pnt1);
        }
        boolean vis[] = new boolean[V];
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        for(int i=0;i<V;++i){
            if(!vis[i]){
                ArrayList<Integer> temp = new ArrayList<>();
                dfs(adj,vis,temp,i);
                res.add(temp);
            }
        }
        return res;
    }
    public void dfs(ArrayList<ArrayList<Integer>> adj,boolean vis[],
        ArrayList<Integer> res,int curr){
        ArrayList<Integer> temp = adj.get(curr);
        vis[curr] = true;
        res.add(curr);
        for(int i:temp){
            if(!vis[i]){
                dfs(adj,vis,res,i);
            }
        }
    }
```