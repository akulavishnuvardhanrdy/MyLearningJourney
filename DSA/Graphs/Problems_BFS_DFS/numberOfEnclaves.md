# Question  

You are given an m x n binary matrix grid, where 0 represents a sea cell and 1 represents a land cell.

A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid.

Return the number of land cells in grid for which we cannot walk off the boundary of the grid in any number of moves.



##### Examples :

Input: grid = [[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]

Output: 3

Explanation: There are three 1s that are enclosed by 0s, and one 1 that is not enclosed because its on the boundary.




### Solve: [https://leetcode.com/problems/number-of-enclaves/](https://leetcode.com/problems/number-of-enclaves/)

*** 

# Optimal Solution 

``` java
    public int numEnclaves(int[][] grid) {
        int count = 0;
        for(int i=0;i<grid.length;++i){
            if(grid[i][0]==1)
                dfs(grid,i,0);
        }
        for(int i=0;i<grid.length;++i){
            if(grid[i][grid[0].length-1]==1)
                dfs(grid,i,grid[0].length-1);
        }
        for(int i=0;i<grid[0].length;++i){
            if(grid[0][i]==1)
                dfs(grid,0,i);
        }
        for(int i=0;i<grid[0].length;++i){
            if(grid[grid.length-1][i]==1)
                dfs(grid,grid.length-1,i);
        }
        for(int i=0;i<grid.length;++i){
            for(int j=0;j<grid[0].length;++j){
                if(grid[i][j]==1)
                    count++;
            }
        }
        return count;
    }
    void dfs(int grid[][],int row,int col){
        grid[row][col] = 0;
        int del[] = new int[]{-1,0,1,0,-1};
        for(int i=1;i<del.length;++i){
            int delrow = row+del[i-1];
            int delcol = col+del[i];
            if(delrow>=0 && delcol>=0 && delrow<grid.length && delcol<grid[0].length && grid[delrow][delcol]!=0){
                dfs(grid,delrow,delcol);
            }
        }
    }
```