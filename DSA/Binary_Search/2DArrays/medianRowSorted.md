# Question

Given a row-wise sorted matrix mat[][] where the number of rows and columns is always odd. Return the median of the matrix.
##### Example 1:

Input: mat[][] = [[1, 3, 5], 
                [2, 6, 9], 
                [3, 6, 9]]

Output: 5

Explanation: Sorting matrix elements gives us [1, 2, 3, 3, 5, 6, 6, 9, 9]. Hence, 5 is median.

***

### Solve: [https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1](https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1)

# Optimal Solution 


``` java
    public int median(int[][] arr) {
        int n= arr.length, m = arr[0].length;
        int min = Integer.MAX_VALUE,max = Integer.MIN_VALUE;
        for(int i=0;i<n;++i){
            if(min>arr[i][0]) min =arr[i][0];
            if(max<arr[i][m-1]) max = arr[i][m-1];
        }
        int med = (m*n)/2+1;
        while(min<=max){
            int mid = min+(max-min)/2;
            int count = 0;
            for(int i=0;i<n;++i){
                count +=upperBound(arr[i],mid);
            }
            if(count<med)
                min = mid+1;
            else 
                max = mid-1;
        }
        return min;
    }
    public int upperBound(int arr[],int target){
        int low =0,high = arr.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(arr[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        return low;
    }
```

### Time Complexity: O(N*logM * log(maxEle - minEle))  
### Space Complexity: O(1) 