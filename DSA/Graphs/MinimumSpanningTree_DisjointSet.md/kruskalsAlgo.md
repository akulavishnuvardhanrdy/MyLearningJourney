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
        Arrays.sort(edges,(a,b)->Integer.compare(a[2],b[2]));
        int rank[] = new int[V];
        int par[] = new int[V];
        int sum = 0;
        for(int i=0;i<V;++i){
            rank[i] = 1;
            par[i] = i;
        }
        for(int edge[]:edges){
            if(unionSet(par,rank,edge[0],edge[1])){
                sum+=edge[2];
            }
        }
        return sum;
    }
    
    int findParent(int par[],int n){
        if(par[n]==n)  
            return n;
        return par[n] = findParent(par,par[n]);
    }
    // Rank Union
    boolean unionSet(int par[],int rank[],int u,int v){
        int pu = findParent(par,u);
        int pv = findParent(par,v);
        if(pu==pv)
            return false;
        if(rank[pu]<rank[pv])
            par[pu] = pv;
        else if(rank[pu]>rank[pv])
            par[pv] = pu;
        else{
            par[pv] = pu;
            rank[pu]++;
        }
        return true;
    }
    // Size Union
    boolean unionSet(int par[],int size[],int u,int v){
        int pu = findParent(par,u);
        int pv = findParent(par,v);
        if(pu==pv)
            return false;
        if(size[pu]<size[pv]){
            par[pu] = pv;
            size[pv] = size[pv]+size[pu];
        }
        else{
            par[pv] = pu;
            size[pu] = size[pv]+size[pu];
        }
        return true;
    }
```