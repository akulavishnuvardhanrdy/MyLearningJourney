# Question

A peak element in a 2D grid is an element that is strictly greater than all of its adjacent neighbors to the left, right, top, and bottom.

Given a 0-indexed m x n matrix mat where no two adjacent cells are equal, find any peak element mat[i][j] and return the length 2 array [i,j].

You may assume that the entire matrix is surrounded by an outer perimeter with the value -1 in each cell.

You must write an algorithm that runs in O(m log(n)) or O(n log(m)) time.

##### Example 1:

Input: mat = [[1,4],[3,2]]

Output: [0,1]

Explanation: Both 3 and 4 are peak elements so [1,0] and [0,1] are both acceptable answers.

***

### Solve: [https://leetcode.com/problems/find-a-peak-element-ii/description/](https://leetcode.com/problems/find-a-peak-element-ii/description/)

# Optimal Solution 


``` java
    public int[] findPeakGrid(int[][] arr) {
        int n = arr.length, m = arr[0].length;
        int low = 0, high = n-1;
        while(low<=high){
            int mid = (high+low)/2;
            int temp = maxIdx(arr[mid]);
            if((mid==0 || arr[mid][temp]>arr[mid-1][temp]) && 
            (mid==n-1 || arr[mid][temp]>arr[mid+1][temp]))
                return new int[]{mid,temp};
            if(mid==0 || arr[mid][temp]>arr[mid-1][temp])
                low = mid+1;
            else
                high = mid-1;
        }
        return new int[]{-1,-1};
    }

    public int maxIdx(int arr[]){
        int max = Integer.MIN_VALUE;
        int maxIdx = -1;
        for(int i=0;i<arr.length;++i){
            if(max<arr[i]){
                max = arr[i];
                maxIdx = i;
            }
        }
        return maxIdx;
    }
```

### Time Complexity: O(N*logM)  
### Space Complexity: O(1) 