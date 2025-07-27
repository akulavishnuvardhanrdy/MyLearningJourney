# Question

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

##### Example:

Input: nums = [2,7,11,15], target = 9

Output: [0,1]

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

### Solve: [https://leetcode.com/problems/maximum-subarray](https://leetcode.com/problems/maximum-subarray)

***

# BruteForce Solution

#### Time Limit Exceeded        

``` java
public int maxSubArray(int[] nums) {
    int maxsum = Integer.MIN_VALUE;
    for(int i=0;i<nums.length;++i){
        int curr = 0;
        for(int j=i;j<nums.length;++j){
            curr+=nums[j];
            if(maxsum<curr)
                maxsum = curr;
        }            
    }
    return maxsum;
}
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)


# Optimal Solution

### Kadans Algorithm

``` java
public int maxSubArray(int[] nums) {
    int maxsum = Integer.MIN_VALUE;
    int curr =0;
    for(int i=0;i<nums.length;++i){
        curr+=nums[i];
        if(maxsum<curr) maxsum=curr;
        if(curr<0) curr=0;                      
    }
    return maxsum;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)