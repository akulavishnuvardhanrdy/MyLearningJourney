# Question  

Given an n x n binary matrix grid, return the length of the shortest clear path in the matrix. If there is no clear path, return -1.

A clear path in a binary matrix is a path from the top-left cell (i.e., (0, 0)) to the bottom-right cell (i.e., (n - 1, n - 1)) such that:

All the visited cells of the path are 0.
All the adjacent cells of the path are 8-directionally connected (i.e., they are different and they share an edge or a corner).
The length of a clear path is the number of visited cells of this path.




##### Examples :

Input: grid = [[0,1],[1,0]]

Output: 2




### Solve: [https://leetcode.com/problems/shortest-path-in-binary-matrix/](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

*** 

# Optimal Solution 

``` java
    public int shortestPathBinaryMatrix(int[][] grid) {
        if(grid[0][0]!=0 || grid[grid.length-1][grid[0].length-1] != 0)
            return -1;
        if(grid.length==1 && grid[0].length==1)
            return 1;
        ArrayDeque<Pairs> q= new ArrayDeque<>();
        int res[][] = new int[grid.length][grid[0].length];
        for(int i=0;i<res.length;++i){
            Arrays.fill(res[i],Integer.MAX_VALUE);
        }
        res[0][0] = 1;
        q.add(new Pairs(0,0,1));
        while(!q.isEmpty()){
            Pairs p = q.pollFirst();
            for(int i=-1;i<=1;++i){
                for(int j=-1;j<=1;++j){
                    if(i==0 && j==0) continue;
                    int delcol = p.col+i;
                    int delrow = p.row+j;
                    if(delrow==grid.length-1 && delcol== grid[0].length-1){
                        return p.dis+1;
                    }
                    if(delcol>=0 && delrow>=0 && delrow<grid.length && delcol<grid[0].length && grid[delrow][delcol]==0){
                        if(res[delrow][delcol]>p.dis+1){
                            res[delrow][delcol] = p.dis+1;
                            q.addLast(new Pairs(delrow,delcol,p.dis+1));
                        }
                    }
                }
            }
        }
        return -1;
    }
    static class Pairs{
        int row;
        int col;
        int dis;
        public Pairs(int row,int col,int dis){
            this.row = row;
            this.col = col;
            this.dis = dis;
        }
    }
```