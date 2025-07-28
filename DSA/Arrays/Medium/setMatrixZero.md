# Question

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.
 

##### Example:


Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]

Output: [[1,0,1],[0,0,0],[1,0,1]]

### Solve: [https://leetcode.com/problems/set-matrix-zeroes/](https://leetcode.com/problems/set-matrix-zeroes/)

***

# Optimal Solution


``` java
    public void setZeroes(int[][] matrix) {
        boolean firstRow = false;
        boolean firstCol = false;
        int n = matrix.length;
        int m = matrix[0].length;
        for(int i=0;i<n;++i){
            for(int j=0;j<m;++j){
                if(matrix[i][j]==0){
                    if(i==0){
                        firstRow = true;
                    }
                    if(j==0){
                        firstCol = true;
                    }
                    if(j!=0 && i!=0){
                        matrix[i][0] = 0;
                        matrix[0][j] = 0;
                    }
                }
            }
        }
        for(int i=1;i<n;++i){
            if(matrix[i][0]==0){
                for(int j=1;j<m;++j)
                    matrix[i][j]=0;
            }
        }
        for(int i=1;i<m;++i){
            if(matrix[0][i]==0){
                for(int j=1;j<n;++j)
                    matrix[j][i]=0;
            }
        }
        if(firstRow){
            for(int i=0;i<m;++i)
                matrix[0][i] = 0;
        }
        if(firstCol){
            for(int i=0;i<n;++i)
                matrix[i][0] = 0;
        }
    }
```

### Time Complexity: O(2*n*m)
### Space Complexity: O(1)