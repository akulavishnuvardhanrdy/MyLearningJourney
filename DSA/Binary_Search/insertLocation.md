# Question
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

 

##### Example 1:

Input: nums = [1,3,5,6], target = 5

Output: 2

***

# Optimal Solution

``` java
    public int searchInsert(int[] nums, int target) {
        int low = 0, high = nums.length-1;
        int pos = -1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<target) 
                low = mid+1;
            else 
                high = mid -1;
        }
        return low;
    }
```


### Time Complexity: O(logN)  
### Space Complexity: O(1) 