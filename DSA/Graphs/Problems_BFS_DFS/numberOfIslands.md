# Question  

Given a grid of size n*m (n is the number of rows and m is the number of columns in the grid) consisting of 'W's (Water) and 'L's (Land). Find the number of islands.

Note: An island is either surrounded by water or the boundary of a grid and is formed by connecting adjacent lands horizontally or vertically or diagonally i.e., in all 8 directions.




##### Examples :

Input: grid[][] = [['L', 'L', 'W', 'W', 'W'], ['W', 'L', 'W', 'W', 'L'], ['L', 'W', 'W', 'L', 'L'], ['W', 'W', 'W', 'W', 'W'], ['L', 'W', 'L', 'L', 'W']]

Output: 4

Explanation:
The image below shows all the 4 islands in the grid.




### Solve: [https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1](https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1)

*** 

# Optimal Solution 

``` java
    public int countIslands(char[][] grid) {
        // Code here
        int n= grid.length;
        int m = grid[0].length;
        boolean vis[][] = new boolean[n][m];
        int count = 0;
        for(int row=0;row<n;++row){
            for(int col=0;col<m;++col){
                if(grid[row][col]=='L' && !vis[row][col]){
                    dfs(grid,vis,row,col);
                    count++;
                }
            }
        }
        return count;
    }
    public void dfs(char[][] grid, boolean[][] vis,int row,int col){
        int n = grid.length;
        int m = grid[0].length;
        vis[row][col] = true;
        for(int delrow=-1;delrow<=1;++delrow){
            for(int delcol=-1;delcol<=1;++delcol){
                int nrow = row+delrow;
                int ncol = col+delcol;
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && grid[nrow][ncol]=='L' && !vis[nrow][ncol]){
                    dfs(grid,vis,nrow,ncol);
                }
            }
        }
    }
```