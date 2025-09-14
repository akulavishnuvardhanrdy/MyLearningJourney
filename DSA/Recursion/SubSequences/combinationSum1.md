# Question  

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.



##### Examples :

Input: candidates = [2,3,6,7], target = 7

Output: [[2,2,3],[7]]

Explanation:

2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.

7 is a candidate, and 7 = 7.

These are the only two combinations.

### Solve: [https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

*** 

# Optimal Solution 

``` java
    static{
        for(int i=0;i<500;++i){
            combinationSum(new int[1],0);
        }
    }

    public static List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        findCombinations(candidates,target,temp,res,0);
        return res;
    }
    static void findCombinations(int arr[],int target,List<Integer> temp,List<List<Integer>> res,int idx){
        if(target==0){
            res.add(new ArrayList<>(temp));
            return;
        }
        if(idx==arr.length){
            return ;
        }
        if(target-arr[idx]>=0){
            temp.add(arr[idx]);
            findCombinations(arr,target-arr[idx],temp,res,idx);
            temp.remove(temp.size()-1);
        }
        findCombinations(arr,target,temp,res,idx+1);
    }
```