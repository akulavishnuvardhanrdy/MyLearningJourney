# Question  

Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.

The distance between two cells sharing a common edge is 1.




##### Examples :

Input: mat = [[0,0,0],[0,1,0],[0,0,0]]

Output: [[0,0,0],[0,1,0],[0,0,0]]




### Solve: [https://leetcode.com/problems/01-matrix/description/](https://leetcode.com/problems/01-matrix/description/)

*** 

# Optimal Solution 

``` java
    public int[][] updateMatrix(int[][] mat) {
        ArrayDeque<int []> q = new ArrayDeque<>();
        int res[][] = new int[mat.length][mat[0].length];
        for(int i=0;i<res.length;++i){
            Arrays.fill(res[i],-1);
        }
        int del[] = new int[]{-1,0,1,0,-1};
        for(int i=0;i<mat.length;++i){
            for(int j=0;j<mat[0].length;++j){
                if(mat[i][j]==0){
                    res[i][j] = 0;
                    q.addLast(new int[]{i,j,0});
                }
            }
        }
        while(!q.isEmpty()){
            int curr[] = q.pollFirst();
            int row = curr[0],col = curr[1], dis = curr[2];
            for(int i=1;i<del.length;++i){
                int nrow = row+del[i-1];
                int ncol = col+del[i];
            if(nrow>=0 && nrow<mat.length && ncol>=0 && ncol<mat[0].length && res[nrow][ncol]==-1){
                    res[nrow][ncol] = dis+1;
                    q.add(new int[]{nrow,ncol,dis+1});
                }
            }
        }
        return res;
    }
```