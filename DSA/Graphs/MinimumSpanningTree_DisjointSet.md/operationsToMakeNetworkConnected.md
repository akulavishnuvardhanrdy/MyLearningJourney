# Question  

There are n computers numbered from 0 to n - 1 connected by ethernet cables connections forming a network where connections[i] = [ai, bi] represents a connection between computers ai and bi. Any computer can reach any other computer directly or indirectly through the network.

You are given an initial computer network connections. You can extract certain cables between two directly connected computers, and place them between any pair of disconnected computers to make them directly connected.

Return the minimum number of times you need to do this in order to make all the computers connected. If it is not possible, return -1.



##### Examples :

Input: n = 4, connections = [[0,1],[0,2],[1,2]]

Output: 1

Explanation: Remove cable between computer 1 and 2 and place between computers 1 and 3.




### Solve: [https://leetcode.com/problems/number-of-operations-to-make-network-connected/](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)

*** 

# Optimal Solution 

``` java
    public int makeConnected(int n, int[][] connections) {
        int E = connections.length;
        int count = 0;
        if(E<n-1)
            return -1;
        int par[] = new int[n];
        int rank[] = new int[n];
        for(int i=0;i<n;++i){
            par[i] = i;
            rank[i] = 1;
        }
        for(int edge[]:connections){
            unionSet(par,rank,edge[0],edge[1]);
        }
        for(int i=0;i<n;++i){
            if(par[i]==i) count++;
        }
        return count-1;
    }
    int find(int par[],int n){
        if(par[n]==n)
            return n;
        return par[n] = find(par,par[n]);
    }
    boolean unionSet(int par[],int rank[],int u,int v){
        int pu = find(par,u);
        int pv = find(par,v);
        if(pu==pv)
            return true;
        if(rank[pu]<rank[pv]){
            par[pu] = pv;
        }
        else if(rank[pu]>rank[pv]){
            par[pv] = pu;
        }
        else{
            par[pv] = pu;
            rank[pu]++;
        }
        return false;
    }
```