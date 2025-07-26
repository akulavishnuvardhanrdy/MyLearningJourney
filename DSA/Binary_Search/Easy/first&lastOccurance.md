# Question
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

##### Example 1:

Input: nums = [5,7,7,8,8,10], target = 8

Output: [3,4]  


### Solve: [https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

***


# Optimal Solution

``` java
    public int[] searchRange(int[] nums, int target) {
        int low = 0, high = nums.length-1;
        int ans[] = new int[2];
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<target)
                low = mid+1;
            else
                high = mid-1;
        }
        if(low>=nums.length || nums[low]!=target) 
            return new int[]{-1,-1};
        ans[0] = low;

        low = 0;
        high = nums.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        ans[1] = high;

        return ans;
  }
```

### Time Complexity: O(2logN)  
### Space Complexity: O(1) 