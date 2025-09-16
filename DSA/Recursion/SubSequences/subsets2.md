# Question  

Given an integer array nums that may contain duplicates, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.



##### Examples :

Input: nums = [1,2,2]

Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]



### Solve: [https://leetcode.com/problems/subsets-ii/](https://leetcode.com/problems/subsets-ii/)

*** 

# Optimal Solution 

``` java
    public static List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        generate(0,nums,temp,res);
        return res;
    }

    static void generate(int idx,int[] nums,List<Integer> temp,List<List<Integer>> res){
        res.add(new ArrayList(temp));
        for(int i=idx;i<nums.length;++i){
            if(i>idx && nums[i-1]==nums[i]){
                continue;
            }
            temp.add(nums[i]);
            generate(i+1,nums,temp,res);
            temp.remove(temp.size()-1);
        }
    }
```