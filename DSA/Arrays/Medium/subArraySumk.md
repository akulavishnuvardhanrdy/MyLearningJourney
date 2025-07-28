# Question

Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.

A subarray is a contiguous non-empty sequence of elements within an array.
 

##### Example:

Input: nums = [1,1,1], k = 2

Output: 2

### Solve: [https://leetcode.com/problems/subarray-sum-equals-k/description/](https://leetcode.com/problems/subarray-sum-equals-k/description/)

***

# Optimal Solution


``` java
    public int subarraySum(int[] nums, int k) {
        Map<Integer,Integer> map = new HashMap<>();
        int count = 0;
        map.put(0,1);
        int sum=0;
        for(int i=0;i<nums.length;++i){
            sum+=nums[i];
            if (map.containsKey(sum - k)) {
                count += map.get(sum - k);
            }
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return count;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)