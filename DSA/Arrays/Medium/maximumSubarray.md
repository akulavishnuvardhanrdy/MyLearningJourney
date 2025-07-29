# Question

Given an integer array nums, find the subarray with the largest sum, and return its sum.

 

##### Example:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]

Output: 6

Explanation: The subarray [4,-1,2,1] has the largest sum 6.

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