# Question

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.
 

##### Example:


Input: nums = [100,4,200,1,3,2]

Output: 4

Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

### Solve: [https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

***

# Optimal Solution


``` java
    public int longestConsecutive(int[] nums) {
        if(nums.length==0) return 0;
        Arrays.sort(nums);
        int max =1,count =1;
        for(int i=0;i<nums.length-1;++i){
            if((nums[i]+1)==nums[i+1]){
                count++;
                max = Math.max(count,max);
            }
            else if(nums[i]==nums[i+1])
                continue;
            else count=1;
        }
        return max;
    }
```

### Time Complexity: O(n* logn)
### Space Complexity: O(1)