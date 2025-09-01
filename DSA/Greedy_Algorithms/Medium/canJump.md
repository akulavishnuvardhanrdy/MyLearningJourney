# Question

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.



##### Example:

Input: nums = [2,3,1,1,4]

Output: true

Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.



### Solve: [https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)

***

# Optimal Solution
        

``` java
    public boolean canJump(int[] nums) {
        if(nums.length==1) return true;
        int currJump = 0;
        int farthest = 0;
        for(int i=0;i<nums.length-1;++i){
            farthest = Math.max(farthest,i+nums[i]);
            if(i==currJump){
                if(currJump==farthest)
                    return false;
                currJump = farthest;
            }
        }
        return true;  
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)