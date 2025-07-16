# Question

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

##### Example:

Input: nums = [2,7,11,15], target = 9

Output: [0,1]

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

***

# BruteForce Solution

``` java
public int[] twoSum(int[] nums, int target) {
    int sum = 0;
    int n = nums.length;
    for(int i=0;i<n;++i){
        for(int j=i+1;j<n;++j){
            if(nums[i]+nums[j]==target)
                return new int[]{i,j};
        }
    }
    return new int[2];
}
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)


# Optimal Solution

``` java
public int[] twoSum(int[] nums, int target) {
    Map<Integer,Integer> map = new HashMap<>();
    for(int i=0;i<nums.length;++i){
        int rem = target - nums[i];
        if(map.containsKey(rem)){
            return new int[]{i,map.get(rem)};
        }
        map.put(nums[i],i);
    }
    return new int[2];
}
```

### Time Complexity: O(n)
### Space Complexity: O(n)