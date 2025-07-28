# Question

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.
 

##### Example:

Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
        
Output: [[7,4,1],[8,5,2],[9,6,3]]

### Solve: [https://leetcode.com/problems/rotate-image/](https://leetcode.com/problems/rotate-image/)

***

# Optimal Solution


``` java
    public void rotate(int[][] matrix) {
        for(int i=0;i<matrix.length;++i){
            for(int j=i+1;j<matrix[0].length;++j){
                swap(matrix,i,j);
            }
        }
        for(int i=0;i<matrix.length;++i){
            reverse(matrix[i]);
        }
    }

    public void swap(int arr[][],int i, int j){
        int temp = arr[i][j];
        arr[i][j] = arr[j][i];
        arr[j][i] = temp;
    }

    public void reverse(int arr[]){
        int i=0,j=arr.length-1;
        while(i<=j){
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            i++;
            j--;
        }
    }
```

### Time Complexity: O(n*m/2)+O(n*logm)
### Space Complexity: O(1)