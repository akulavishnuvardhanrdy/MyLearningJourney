# Question  
You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return the single element that appears only once.

Your solution must run in O(log n) time and O(1) space.

 

##### Example 1:

Input: nums = [1,1,2,3,3,4,4,8,8]

Output: 2  

***:   


# Optimal Solution  
``` java
    public int singleNonDuplicate(int[] nums) {
        int n = nums.length;
        if(n==1)
            return nums[0];
        if(nums[0]!=nums[1])
            return nums[0];
        if(nums[n-2]!=nums[n-1])
            return nums[n-1];
        int low = 1, high = n-2;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(mid%2==0 && nums[mid+1]==nums[mid] || mid%2!=0 && nums[mid]==nums[mid-1])
                low=mid+1;
            else if(mid%2==0 && nums[mid-1]==nums[mid] || mid%2!=0 && nums[mid]==nums[mid+1])
                high=mid-1;
            else
                return nums[mid];
        }
        return -1;
    }
```

### Time Complexity: O(logN)  
### Space Complexity: O(1) 