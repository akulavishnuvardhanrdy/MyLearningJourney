# Question  

You are given an image represented by an m x n grid of integers image, where image[i][j] represents the pixel value of the image. You are also given three integers sr, sc, and color. Your task is to perform a flood fill on the image starting from the pixel image[sr][sc].

To perform a flood fill:

Begin with the starting pixel and change its color to color.
Perform the same process for each pixel that is directly adjacent (pixels that share a side with the original pixel, either horizontally or vertically) and shares the same color as the starting pixel.
Keep repeating this process by checking neighboring pixels of the updated pixels and modifying their color if it matches the original color of the starting pixel.
The process stops when there are no more adjacent pixels of the original color to update.
Return the modified image after performing the flood fill.



##### Examples :

Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2

Output: [[2,2,2],[2,2,0],[2,0,1]]




### Solve: [https://leetcode.com/problems/flood-fill/](https://leetcode.com/problems/flood-fill/)

*** 

# Optimal Solution 

``` java
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        ArrayDeque<int []> q = new ArrayDeque<>();
        q.add(new int[]{sr,sc,image[sr][sc]});
        image[sr][sc] = color;
        while(!q.isEmpty()){
            int len = q.size();
            for(int k=0;k<len;++k){
                int[] curr = q.pollFirst();
                int i=curr[0],j = curr[1],prev = curr[2];
                if(i>0 && image[i-1][j]==prev && image[i-1][j]!=color){
                    q.add(new int[]{i-1,j,image[i-1][j]});
                    image[i-1][j] = color;
                }
                if(i<image.length-1 && image[i+1][j]==prev && image[i+1][j]!=color){
                    q.add(new int[]{i+1,j,image[i+1][j]});
                    image[i+1][j] = color;                    
                }
                if(j>0 && image[i][j-1]==prev && image[i][j-1]!=color){
                    q.add(new int[]{i,j-1,image[i][j-1]});
                    image[i][j-1] = color;
                }
                if(j<image[0].length-1 && image[i][j+1]==prev && image[i][j+1]!=color){
                    q.add(new int[]{i,j+1,image[i][j+1]});
                    image[i][j+1] = color;
                }
            }            
        }
        return image;
    }
```