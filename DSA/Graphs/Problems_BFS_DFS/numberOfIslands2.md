# Question  

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.




##### Examples :

Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]

Output: 1




### Solve: [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

*** 

# Optimal Solution 

``` java
    public int numIslands(char[][] grid) {
        boolean vis[][] = new boolean[grid.length][grid[0].length];
        int count = 0;
        for(int i=0;i<grid.length;++i){
            for(int j=0;j<grid[0].length;++j){
                if(grid[i][j]=='1' && !vis[i][j]){
                    dfs(grid,vis,i,j);
                    count++;
                }
            }
        }
        return count;
    }
    void dfs(char grid[][],boolean vis[][],int i,int j){
        vis[i][j] = true;
        int temp[] = new int[]{-1,0,1,0,-1};
        for(int k=1;k<temp.length;++k){
            int row = i+temp[k-1];
            int col = j+temp[k];
            if(row>=0 && col>=0 && row<grid.length && col<grid[0].length && !vis[row][col] && grid[row][col]=='1'){
                    dfs(grid,vis,row,col);
                }
        }
    }
```