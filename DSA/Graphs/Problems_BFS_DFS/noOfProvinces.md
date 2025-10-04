# Question  

There are n cities. Some of them are connected, while some are not. If city a is connected directly with city b, and city b is connected directly with city c, then city a is connected indirectly with city c.

A province is a group of directly or indirectly connected cities and no other cities outside of the group.

You are given an n x n matrix isConnected where isConnected[i][j] = 1 if the ith city and the jth city are directly connected, and isConnected[i][j] = 0 otherwise.

Return the total number of provinces.



##### Examples :

Input: isConnected = [[1,1,0],[1,1,0],[0,0,1]]

Output: 2




### Solve: [https://leetcode.com/problems/number-of-provinces/](https://leetcode.com/problems/number-of-provinces/)

*** 

# Optimal Solution 

``` java
    public int findCircleNum(int[][] isConnected) {
        int count = 0;
        boolean vis[] = new boolean[isConnected.length];
        for(int i=0;i<isConnected.length;++i){
            if(!vis[i]){
                dfs(isConnected,vis,i);
                count++;
            }
        }
        return count;
    }
    public void dfs(int[][] adj,boolean vis[],int curr){
        int temp[] = adj[curr]; 
        vis[curr] = true;
        for(int i=0;i<temp.length;++i){
            if(temp[i]==1 && !vis[i]){
                dfs(adj,vis,i);
            }
        }
    }
```