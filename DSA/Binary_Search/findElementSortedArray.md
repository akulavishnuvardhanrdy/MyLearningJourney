# Question

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.
 

##### Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9

Output: 4

Explanation: 9 exists in nums and its index is 4

***

# Optimal Solution 


``` java
    public int search(int[] nums, int target) {
        return BinarySearch(nums,target,0,nums.length-1);
    }
    int BinarySearch(int nums[],int target,int left,int right){
        if(left>right) return -1;
        int mid = (left+right)/2;
        if(nums[mid]==target)
            return mid;
        else if(nums[mid]<target)
            return BinarySearch(nums,target,mid+1,right);
        else
            return BinarySearch(nums,target,left,mid-1);
    }
```

### Time Complexity: O(logN)  
### Space Complexity: O(logN) 