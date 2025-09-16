# Question  

Consider a rat placed at position (0, 0) in an n x n square matrix mat[][]. The rat's goal is to reach the destination at position (n-1, n-1). The rat can move in four possible directions: 'U'(up), 'D'(down), 'L' (left), 'R' (right).

The matrix contains only two possible values:

0: A blocked cell through which the rat cannot travel.
1: A free cell that the rat can pass through.
Your task is to find all possible paths the rat can take to reach the destination, starting from (0, 0) and ending at (n-1, n-1), under the condition that the rat cannot revisit any cell along the same path. Furthermore, the rat can only move to adjacent cells that are within the bounds of the matrix and not blocked.
If no path exists, return an empty list.

Note: Return the final result vector in lexicographically smallest order.



##### Examples :

Input: mat[][] = [[1, 0, 0, 0], [1, 1, 0, 1], [1, 1, 0, 0], [0, 1, 1, 1]]

Output: ["DDRDRR", "DRDDRR"]

Explanation: The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.



### Solve: [https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

*** 

# Optimal Solution 

``` java
    public ArrayList<String> ratInMaze(int[][] maze) {
        // code here
        ArrayList<String> res = new ArrayList<>();
        boolean visited[][] = new boolean[maze.length][];
        for(int i=0;i<maze.length;++i){
            visited[i] = new boolean[maze.length];
        }
        StringBuilder sb = new StringBuilder();
        visited[0][0] = true;
        findPath(maze,res,sb,0,0,visited);
        Collections.sort(res);
        return res;
    }
    void findPath(int maze[][], ArrayList<String> res,
            StringBuilder sb,int x,int y,boolean visited[][]){
        if(x==maze.length-1 && y==maze.length-1){
            res.add(sb.toString());
            return ;
        }
        if(x<maze.length-1 && maze[x+1][y]==1 && !visited[x+1][y]){
            sb.append("D");
            visited[x+1][y] = true;
            findPath(maze,res,sb,x+1,y,visited);
            visited[x+1][y] = false;
            sb.setLength(sb.length()-1);
        }
        if(y<maze.length-1 && maze[x][y+1]==1 && !visited[x][y+1]){
            sb.append("R");
            visited[x][y+1] = true;
            findPath(maze,res,sb,x,y+1,visited);
            visited[x][y+1] = false;
            sb.setLength(sb.length()-1);
        }
        if(x>0 && maze[x-1][y]==1 && !visited[x-1][y]){
            sb.append("U");
            visited[x-1][y] = true;
            findPath(maze,res,sb,x-1,y,visited);
            visited[x-1][y] = false;
            sb.setLength(sb.length()-1);
        }
        if(y>0 && maze[x][y-1]==1 && !visited[x][y-1]){
            sb.append("L");
            visited[x][y-1] = true;
            findPath(maze,res,sb,x,y-1,visited);
            visited[x][y-1] = false;
            sb.setLength(sb.length()-1);
        }
    }
```