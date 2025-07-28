# Question

Given an m x n matrix, return all elements of the matrix in spiral order.
 

##### Example:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]

Output: [1,2,3,6,9,8,7,4,5]

### Solve: [https://leetcode.com/problems/spiral-matrix/](https://leetcode.com/problems/spiral-matrix/)

***

# Optimal Solution


``` java
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ls = new ArrayList<>();
        int left =0,right =matrix[0].length-1;
        int top =0,bottom = matrix.length-1;
        while(top<=bottom && left<=right){
            for(int i=left;i<=right;++i){
                ls.add(matrix[top][i]);
            }
            top++;
            for(int i=top;i<=bottom;++i){
                ls.add(matrix[i][right]);
            }
            right--;
            if(top<=bottom){
                for(int i=right;i>=left;--i){
                    ls.add(matrix[bottom][i]);
                }
                bottom--;
            }
            if(left<=right){
                for(int i=bottom;i>=top;--i){
                    ls.add(matrix[i][left]);
                }
                left++;
            }
        }
        return ls;
    }
```

### Time Complexity: O(n * m)
### Space Complexity: O(n * m)