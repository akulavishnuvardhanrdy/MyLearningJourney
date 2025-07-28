# Question

You are given an array arr[] of integers. Your task is to find the maximum sum of the smallest and second smallest elements across all subarrays (of size >= 2) of the given array.
 

##### Example:

Input: arr[] = [4, 3, 5, 1]

Output: 8

Explanation: All subarrays with at least 2 elements and find the two smallest numbers in each:
[4, 3] → 3 + 4 = 7
[4, 3, 5] → 3 + 4 = 7
[4, 3, 5, 1] → 1 + 3 = 4
[3, 5] → 3 + 5 = 8
[3, 5, 1] → 1 + 3 = 4
[5, 1] → 1 + 5 = 6
Maximum Score is 8.

### Solve: [https://www.geeksforgeeks.org/problems/max-sum-in-sub-arrays0824/1](https://www.geeksforgeeks.org/problems/max-sum-in-sub-arrays0824/1)

***

# Optimal Solution


``` java
    public int maxSum(int arr[]) {
        int res = 0;
        for(int i=1;i<arr.length;++i){
            res = Math.max(res,arr[i]+arr[i-1]);
        }
        return res;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)