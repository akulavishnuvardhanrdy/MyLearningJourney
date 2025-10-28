# Question  

Given a boolean 2D matrix grid of size n * m. You have to find the number of distinct islands where a group of connected 1s (horizontally or vertically) forms an island. Two islands are considered to be distinct if and only if one island is not equal to another (not rotated or reflected).



##### Examples :

Input:
grid[][] = [[1, 1, 0, 0, 0],
            [1, 1, 0, 0, 0],
            [0, 0, 0, 1, 1],
            [0, 0, 0, 1, 1]]

Output: 1

Explanation:
grid[][] = [[1, 1, 0, 0, 0], 
            [1, 1, 0, 0, 0], 
            [0, 0, 0, 1, 1], 
            [0, 0, 0, 1, 1]]
Same colored islands are equal. We have 2 equal islands, so we have only 1 distinct island.




### Solve: [https://www.geeksforgeeks.org/problems/number-of-distinct-islands/1](https://www.geeksforgeeks.org/problems/number-of-distinct-islands/1)

*** 

# Optimal Solution 

``` java
    int countDistinctIslands(int[][] grid) {
        Set<ArrayList<String>> set = new HashSet<>();
        for(int i=0;i<grid.length;++i){
            for(int j=0;j<grid[0].length;++j){
                if(grid[i][j]==1){
                    ArrayList<String> temp = new ArrayList<>();
                    bfs(grid,temp,i,j);
                    set.add(temp);
                }
            }
        }
        return set.size();
    }
    void bfs(int grid[][],ArrayList<String> res,int row,int col){
        grid[row][col] = 0;
        res.add("00");
        ArrayDeque<int[]> q = new ArrayDeque<>();
        q.addLast(new int[]{row,col});
        while(!q.isEmpty()){
            int curr[] = q.pollFirst();
            int i = curr[0],j = curr[1];
            int del[] = new int[]{-1,0,1,0,-1};
            for(int k=1;k<del.length;++k){
                int delrow = i+del[k-1];
                int delcol = j+del[k];
                if(delrow>=0 && delcol>=0 && delcol<grid[0].length && delrow<
                grid.length && grid[delrow][delcol]==1){
                    res.add((delrow-row)+""+(delcol-col));
                    grid[delrow][delcol] = 0;
                    q.addLast(new int[]{delrow,delcol});
                }
            }
        }
    }
```