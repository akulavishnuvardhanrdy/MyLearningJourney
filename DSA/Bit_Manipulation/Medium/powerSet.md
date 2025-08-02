# Question

Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

##### Example:

Input: nums = [1,2,3]

Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]


### Solve: [https://leetcode.com/problems/subsets/description/](https://leetcode.com/problems/subsets/description/)
   


# Optimal Solution:  
``` java
    public List<List<Integer>> subsets(int[] nums) {
        int total = 1<<nums.length;
        List<List<Integer>> res = new ArrayList<>();
        for(int i=0;i<total;++i){
            List<Integer> temp = new ArrayList<>();
            int curr = i;
            for(int j=nums.length-1;j>=0;--j){
                if((curr&1)==1){
                    temp.add(nums[j]);
                }
                curr>>=1;
            }
            res.add(temp);
        }
        return res;
    }
```
### Time Complexity: O(N*2^N) N-Greater No:of bits  
### Space Complexity: O(1) 