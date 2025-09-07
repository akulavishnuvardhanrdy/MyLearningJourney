# Question

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.



##### Example:

Input: nums = [1,2,3,1]

Output: 4

Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.




### Solve: [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)
   


# Optimal Solution:  


``` java
    public int rob(int[] nums) {
        int res[] = new int[nums.length];
        if(nums.length==1) return nums[0];
        res[0] = nums[0];
        res[1] = Math.max(nums[1],nums[0]);
        for(int i=2;i<nums.length;++i){
            res[i] = Math.max(nums[i]+res[i-2],res[i-1]);
        }
        return res[res.length-1];
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)