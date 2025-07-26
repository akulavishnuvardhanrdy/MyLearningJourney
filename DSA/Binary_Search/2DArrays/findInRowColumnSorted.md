# Question

Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.

##### Example 1:

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5

Output: true

***

### Solve: [https://leetcode.com/problems/search-a-2d-matrix-ii/description/](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)

# Optimal Solution 


``` java
    public boolean searchMatrix(int[][] matrix, int target) {
        int n= matrix.length,m= matrix[0].length;
        int i=0,j=m-1;
        while(i<n && j>=0){
            int val = matrix[i][j];
            if(val == target)
                return true;
            else if(val < target)
                i++;
            else
                j--;
        }
        return false;
    }
```

### Time Complexity: O(M+N)  
### Space Complexity: O(1) 