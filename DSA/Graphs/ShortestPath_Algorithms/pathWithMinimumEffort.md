# Question  

You are a hiker preparing for an upcoming hike. You are given heights, a 2D array of size rows x columns, where heights[row][col] represents the height of cell (row, col). You are situated in the top-left cell, (0, 0), and you hope to travel to the bottom-right cell, (rows-1, columns-1) (i.e., 0-indexed). You can move up, down, left, or right, and you wish to find a route that requires the minimum effort.

A route's effort is the maximum absolute difference in heights between two consecutive cells of the route.

Return the minimum effort required to travel from the top-left cell to the bottom-right cell.



##### Examples :

Input: heights = [[1,2,2],[3,8,2],[5,3,5]]

Output: 2

Explanation: The route of [1,3,5,3,5] has a maximum absolute difference of 2 in consecutive cells.
This is better than the route of [1,2,2,2,5], where the maximum absolute difference is 3.




### Solve: [https://leetcode.com/problems/path-with-minimum-effort/](https://leetcode.com/problems/path-with-minimum-effort/)

*** 

# Optimal Solution 

``` java
    public int minimumEffortPath(int[][] heights) {
        if(heights.length==1 && heights[0].length==1)
            return 0;
        int res[][] = new int[heights.length][heights[0].length];
        PriorityQueue<Pairs> q = new PriorityQueue<>(
            (a,b)->a.diff-b.diff
        );
        int del[] = new int[]{-1,0,1,0,-1};
        for(int i=0;i<heights.length;++i){
            Arrays.fill(res[i],Integer.MAX_VALUE);
        }
        q.add(new Pairs(0,0,0));
        while(!q.isEmpty()){
            Pairs p = q.poll();
            if(p.diff>res[p.row][p.col])
                continue;
            if(p.row==heights.length-1 && p.col==heights[0].length-1)
                return p.diff;
            for(int i=1;i<del.length;++i){
                int delrow = del[i-1]+p.row;
                int delcol = del[i]+p.col;
                if(delcol>=0 && delrow>=0 && delrow<heights.length && delcol<heights[0].length){
                    int absDiff = Math.max(p.diff,Math.abs(heights[p.row][p.col]-heights[delrow][delcol]));
                    if(absDiff<res[delrow][delcol]){
                        res[delrow][delcol] = absDiff;
                        q.add(new Pairs(delrow,delcol,absDiff));
                    }
                }
            }
        }
        return res[heights.length-1][heights[0].length-1];
    }
    static class Pairs{
        int row;
        int col;
        int diff;
        public Pairs(int row,int col,int diff){
            this.row = row;
            this.col = col;
            this.diff = diff;
        }
    }
```