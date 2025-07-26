# Question

You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.


Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

##### Example 1:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3

Output: true

***

### Solve: [https://leetcode.com/problems/search-a-2d-matrix/description/](https://leetcode.com/problems/search-a-2d-matrix/description/)

# Optimal Solution 


``` java
    public boolean searchMatrix(int[][] matrix, int target) {
        int n = matrix.length, m = matrix[0].length;
        int low = 0, high = n*m-1;
        while(low<=high){
            int mid = (low+high)/2;
            int ele = matrix[mid/m][mid%m];
            if(ele == target)
                return true;
            else if (ele < target)  
                low = mid+1;
            else
                high = mid-1;
        }
        return false;
    }
```

### Time Complexity: O(M+N)  
### Space Complexity: O(1) 