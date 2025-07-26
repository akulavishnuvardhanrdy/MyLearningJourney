# Question

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.
 

##### Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9

Output: 4

Explanation: 9 exists in nums and its index is 4

***

### Solve: [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)

# Optimal Solution 


``` java
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]==target)
                return mid;
            if(nums[mid]<target)
                low = mid+1;
            else
                high = mid-1;
        }
        return -1;
    }
```

### Time Complexity: O(logN)  
### Space Complexity: O(logN) 