# Question  

Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.





##### Examples :

Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"

Output: true



### Solve: [https://leetcode.com/problems/word-search/](https://leetcode.com/problems/word-search/)

*** 

# Optimal Solution 

``` java
    public boolean exist(char[][] board, String word) {
        StringBuilder sb  = new StringBuilder();
        char start  = word.charAt(0);
        sb.append(start);
        boolean visited[][] = new boolean[board.length][];
        for(int i=0;i<board.length;++i){
            visited[i] = new boolean[board[0].length];
            for(int j=0;j<board[0].length;++j){
                visited[i][j] = false;
            }
        }
        for(int i=0;i<board.length;++i){
            for(int j =0;j<board[0].length;++j){
                if(board[i][j]==start){
                    visited[i][j] = true;
                    if(findValid(board,word,visited,sb,i,j,1))
                        return true;
                    visited[i][j] = false;
                }
            }
        }
        return false;
    }
    boolean findValid(char board[][],String word,boolean[][] visited,StringBuilder sb,int x,int y,int idx){
        if(sb.length()==word.length())
            return true;
        if(x>0 && !visited[x-1][y] && board[x-1][y]==word.charAt(idx)){
            sb.append(board[x-1][y]);
            visited[x-1][y] = true;
            if(findValid(board,word,visited,sb,x-1,y,idx+1))
                return true;
            sb.setLength(sb.length()-1);
            visited[x-1][y] = false;
        }
        if(x<board.length-1 && !visited[x+1][y] && board[x+1][y]==word.charAt(idx)){
            sb.append(board[x+1][y]);
            visited[x+1][y] = true;
            if(findValid(board,word,visited,sb,x+1,y,idx+1))
                return true;
            sb.setLength(sb.length()-1);
            visited[x+1][y] = false;
        }
        if(y>0 && !visited[x][y-1] && board[x][y-1]==word.charAt(idx)){
            sb.append(board[x][y-1]);
            visited[x][y-1] = true;
            if(findValid(board,word,visited,sb,x,y-1,idx+1))
                return true;
            sb.setLength(sb.length()-1);
            visited[x][y-1] = false;
        }
        if(y<board[0].length-1 && !visited[x][y+1] && board[x][y+1]==word.charAt(idx)){
            visited[x][y+1] = true;
            sb.append(board[x][y+1]);
            if(findValid(board,word,visited,sb,x,y+1,idx+1))
                return true;
            sb.setLength(sb.length()-1);
            visited[x][y+1] = false;
        }
        return false;
    }
```