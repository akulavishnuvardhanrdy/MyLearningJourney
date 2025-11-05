# Question  

You are given an n x n binary matrix grid. You are allowed to change at most one 0 to be 1.

Return the size of the largest island in grid after applying this operation.

An island is a 4-directionally connected group of 1s.



##### Examples :

Input: grid = [[1,0],[0,1]]

Output: 3

Explanation: Change one 0 to 1 and connect two 1s, then we get an island with area = 3.




### Solve: [https://leetcode.com/problems/making-a-large-island/](https://leetcode.com/problems/making-a-large-island/)

*** 

# Optimal Solution 

``` java
class Solution {
    public int largestIsland(int[][] grid) {
        int n = grid.length, m = grid[0].length;
        UnionFind ds = new UnionFind(n*m);
        int max = Integer.MIN_VALUE;
        int del[] = new int[]{-1,0,1,0,-1};
        Set<Integer> set = new HashSet<>();
        for(int i=0;i<n;++i){
            for(int j=0;j<m;++j){
                if(grid[i][j]==1){
                    int idx = i*m+j;
                    for(int k=1;k<del.length;++k){
                        int delrow = i+del[k-1];
                        int delcol = j+del[k];
                        int curr = delrow*m+delcol;
                        if(delrow>=0 && delcol>=0 && delrow<n && delcol<m && grid[delrow][delcol]==1){
                            ds.union(idx,curr);
                        }
                    }
                }
            }
        }
        for(int row=0;row<n;++row){
            for(int col=0;col<m;++col){
                if(grid[row][col]==0){
                    int curr = 1;
                    for(int k=1;k<del.length;++k){
                        int delrow = row+del[k-1];
                        int delcol = col+del[k];
                        int idx = delrow*m+delcol;
                        if(delrow>=0 && delcol>=0 && delrow<n && delcol<m && grid[delrow][delcol]==1){
                            set.add(ds.find(idx));
                        }
                    }
                    for(int num:set){
                        curr+=ds.findSize(num);
                    }
                    if(curr>max)
                        max = curr;
                    set.clear();
                }
            }
        }
        return max==Integer.MIN_VALUE?m*n:max;
    }
}

class UnionFind{
    int par[],size[];
    UnionFind(int n){
        par = new int[n];
        size = new int[n];
        for(int i=0;i<n;++i){
            par[i] = i;
            size[i] = 1;
        }
    }
    int find(int n){
        if(par[n]==n)
            return n;
        return par[n] = find(par[n]);
    }
    boolean union(int u,int v){
        int pu = find(u);
        int pv = find(v);
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
    int findSize(int n){
        return size[find(n)];
    }
}
```