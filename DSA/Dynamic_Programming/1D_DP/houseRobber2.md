# Question

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.


##### Example:

Input: nums = [2,3,2]

Output: 3

Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.



### Solve: [https://leetcode.com/problems/house-robber-ii/](https://leetcode.com/problems/house-robber-ii/)
   


# Optimal Solution:  


``` java
    public int rob(int[] nums) {
        int res[] = new int[nums.length];
        if(nums.length==1) return nums[0];
        if(nums.length==2) return Math.max(nums[0],nums[1]);

        res[0] = nums[0];
        res[1] = Math.max(nums[1],nums[0]);
        for(int i=2;i<nums.length-1;++i){
            res[i] = Math.max(nums[i]+res[i-2],res[i-1]);
        }
        int temp1 = res[res.length-2];
        
        res[1] = nums[1];
        res[2] = Math.max(nums[1],nums[2]);
        for(int i=3;i<nums.length;++i){
            res[i] = Math.max(nums[i]+res[i-2],res[i-1]);
        }
        return Math.max(temp1,res[res.length-1]);
    }
```
### Time Complexity: O(2*n)
### Space Complexity: O(n)