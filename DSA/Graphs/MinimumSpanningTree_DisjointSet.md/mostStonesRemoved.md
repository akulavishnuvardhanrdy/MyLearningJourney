# Question  

On a 2D plane, we place n stones at some integer coordinate points. Each coordinate point may have at most one stone.

A stone can be removed if it shares either the same row or the same column as another stone that has not been removed.

Given an array stones of length n where stones[i] = [xi, yi] represents the location of the ith stone, return the largest possible number of stones that can be removed.



##### Examples :

Input: stones = [[0,0],[0,1],[1,0],[1,2],[2,1],[2,2]]

Output: 5

Explanation: One way to remove 5 stones is as follows:
1. Remove stone [2,2] because it shares the same row as [2,1].
2. Remove stone [2,1] because it shares the same column as [0,1].
3. Remove stone [1,2] because it shares the same row as [1,0].
4. Remove stone [1,0] because it shares the same column as [0,0].
5. Remove stone [0,1] because it shares the same row as [0,0].
Stone [0,0] cannot be removed since it does not share a row/column with another stone still on the plane.



### Solve: [https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/)

*** 

# Optimal Solution 

``` java
class Solution {
    public int removeStones(int[][] stones) {
        int offset = 10001;
        UnionFind ds = new UnionFind(20002);
        Set<Integer> set = new HashSet<>();
        for(int stone[]:stones){
            int row = stone[0];
            int col = stone[1]+offset;
            ds.union(row,col);
            set.add(row);
            set.add(col);
        }
        int components=0;
        for(int node:set){
            if(ds.find(node)==node)
                components++;
        }
        return stones.length-components;
    }
}
class UnionFind{
    int par[],rank[];
    UnionFind(int n){
        par = new int[n];
        rank = new int[n];
        for(int i=0;i<n;++i){
            par[i] = i;
            rank[i] = 1;
        }
    }
    int find(int n){
        if(par[n]==n)
            return n;
        return par[n] = find(par[n]);
    }
    void union(int u,int v){
        int pu = find(u);
        int pv = find(v);
        if(pu==pv)
            return ;
        if(rank[pu]<rank[pv])
            par[pu] = pv;
        else if(rank[pu]>rank[pv])
            par[pv] = pu;
        else{
            par[pv] = pu;
            rank[pu]++;
        }
    }
}
```