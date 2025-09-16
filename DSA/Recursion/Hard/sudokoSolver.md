# Question  

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy all of the following rules:

Each of the digits 1-9 must occur exactly once in each row.
Each of the digits 1-9 must occur exactly once in each column.
Each of the digits 1-9 must occur exactly once in each of the 9 3x3 sub-boxes of the grid.
The '.' character indicates empty cells.



##### Examples :

Input: board = [["5","3",".",".","7",".",".",".","."],["6",".",".","1","9","5",".",".","."],[".","9","8",".",".",".",".","6","."],["8",".",".",".","6",".",".",".","3"],["4",".",".","8",".","3",".",".","1"],["7",".",".",".","2",".",".",".","6"],[".","6",".",".",".",".","2","8","."],[".",".",".","4","1","9",".",".","5"],[".",".",".",".","8",".",".","7","9"]]

Output: [["5","3","4","6","7","8","9","1","2"],["6","7","2","1","9","5","3","4","8"],["1","9","8","3","4","2","5","6","7"],["8","5","9","7","6","1","4","2","3"],["4","2","6","8","5","3","7","9","1"],["7","1","3","9","2","4","8","5","6"],["9","6","1","5","3","7","2","8","4"],["2","8","7","4","1","9","6","3","5"],["3","4","5","2","8","6","1","7","9"]]



### Solve: [https://leetcode.com/problems/sudoku-solver/](https://leetcode.com/problems/sudoku-solver/)

*** 

# Optimal Solution 

``` java
    public void solveSudoku(char[][] board) {
        solve(board);
    }
    boolean solve(char board[][]){
        for(int i=0;i<9;++i){
            for(int j=0;j<9;++j){
                if(board[i][j]=='.'){
                    for(char temp='1';temp<='9';++temp){
                        if(isValidSudoko(board,i,j,temp)){
                            board[i][j]=temp;
                            if(solve(board))
                                return true;
                            board[i][j]='.';
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }
    boolean isValidSudoko(char[][] board,int row, int col, char temp){
        for(int i=0;i<9;++i){
            if(board[row][i]==temp)
                return false;
            if(board[i][col]==temp)
                return false;
        }
        int startcol = (col/3)*3;
        int startrow = (row/3)*3;
        for(int i=startrow;i<startrow+3;++i){
            for(int j=startcol;j<startcol+3;++j){
                if(board[i][j]==temp)
                    return false;
            }
        }
        return true;
    }
```