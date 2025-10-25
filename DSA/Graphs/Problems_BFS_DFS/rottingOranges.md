# Question  

You are given an m x n grid where each cell can have one of three values:

0 representing an empty cell,
1 representing a fresh orange, or
2 representing a rotten orange.
Every minute, any fresh orange that is 4-directionally adjacent to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return -1.




##### Examples :

Input: grid = [[2,1,1],[1,1,0],[0,1,1]]

Output: 4




### Solve: [https://leetcode.com/problems/rotting-oranges/](https://leetcode.com/problems/rotting-oranges/)

*** 

# Optimal Solution 

``` java
    public int orangesRotting(int[][] grid) {
        int fresh = 0;
        int time = 0;
        ArrayDeque<int[]> q = new ArrayDeque<>();
        for(int i=0;i<grid.length;++i){
            for(int j=0;j<grid[0].length;++j){
                if(grid[i][j]==1)
                    fresh++;
                if(grid[i][j]==2){
                    q.addLast(new int[]{i,j});
                }
            }
        }
        if(fresh==0) return 0; 
        while(!q.isEmpty()){
            int len = q.size();
            boolean rotten = false;
            for(int k=0;k<len;++k){
                int[] curr = q.pollFirst();
                int i = curr[0],j = curr[1];
                if(helper(grid,q,i-1,j)){
                    fresh--;
                    rotten = true;
                }
                if(helper(grid,q,i+1,j)){
                    fresh--;
                    rotten = true;
                }
                if(helper(grid,q,i,j-1)){
                    fresh--;
                    rotten = true;
                }
                if(helper(grid,q,i,j+1)){
                    fresh--;
                    rotten = true;
                }
            }
            if(rotten)
                time++;
        }
        return fresh==0 ?time:-1;
    }
    boolean helper(int[][] arr,ArrayDeque<int []> q,int i,int j){
        if(i<0 || j<0 || j>=arr[0].length || i>=arr.length)
            return false;
        if(arr[i][j]!=1)
            return false;
        arr[i][j] = 2;
        q.addLast(new int[]{i,j});
        return true;
    }
```