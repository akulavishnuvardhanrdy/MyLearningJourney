# Question  

You are given an m x n matrix board containing letters 'X' and 'O', capture regions that are surrounded:

Connect: A cell is connected to adjacent cells horizontally or vertically.
Region: To form a region connect every 'O' cell.
Surround: The region is surrounded with 'X' cells if you can connect the region with 'X' cells and none of the region cells are on the edge of the board.
To capture a surrounded region, replace all 'O's with 'X's in-place within the original board. You do not need to return anything.



##### Examples :

Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]

Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]

Explanation:


In the above diagram, the bottom region is not captured because it is on the edge of the board and cannot be surrounded.




### Solve: [https://leetcode.com/problems/surrounded-regions/](https://leetcode.com/problems/surrounded-regions/)

*** 

# Optimal Solution 

``` java
    public void solve(char[][] board) {
        boolean vis[][] = new boolean[board.length][board[0].length];
        for(int i=0;i<board.length;++i){
            if(board[i][0]=='O')
                dfs(board,vis,i,0);
        }
        for(int i=0;i<board.length;++i){
            if(board[i][board[0].length-1]=='O')
                dfs(board,vis,i,board[0].length-1);
        }
        for(int i=0;i<board[0].length;++i){
            if(board[0][i]=='O')
                dfs(board,vis,0,i);
        }
        for(int i=0;i<board[0].length;++i){
            if(board[board.length-1][i]=='O')
                dfs(board,vis,board.length-1,i);
        }
        for(int i=0;i<board.length;++i){
            for(int j=0;j<board[0].length;++j){
                if(board[i][j]=='O' && !vis[i][j])
                    board[i][j] = 'X';
            }
        }
    }
    void dfs(char board[][],boolean vis[][],int row,int col){
        vis[row][col] = true;
        int del[] = new int[]{-1,0,1,0,-1};
        for(int i=1;i<del.length;++i){
            int delrow = row+del[i-1];
            int delcol = col+del[i];
            if(delrow>=0 && delcol>=0 && delrow<board.length && delcol<board[0].length && !vis[delrow][delcol] && board[delrow][delcol]=='O'){
                dfs(board,vis,delrow,delcol);
            }
        }
    }
```