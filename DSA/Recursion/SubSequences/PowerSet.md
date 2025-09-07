# Question

Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.



##### Example:

Input: nums = [1,2,3]

Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]


### Solve: [https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)
   


# Optimal Solution:  
``` java
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        generate(0,nums,temp,res);
        return res;
    }
    void generate(int idx,int[] nums,List<Integer> temp,List<List<Integer>> res){
        if(idx==nums.length){
            res.add(new ArrayList(temp));
            return ;
        }
        temp.add(nums[idx]);
        generate(idx+1,nums,temp,res);
        temp.remove(temp.size()-1);
        generate(idx+1,nums,temp,res);
    }
```
### Time Complexity: O(2^n *n)  
### Space Complexity: O(n) 