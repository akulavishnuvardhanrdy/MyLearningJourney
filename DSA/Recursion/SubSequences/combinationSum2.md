# Question  

Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.



##### Examples :

Input: candidates = [10,1,2,7,6,1,5], target = 8

Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]



### Solve: [https://leetcode.com/problems/combination-sum-ii/](https://leetcode.com/problems/combination-sum-ii/)

*** 

# Optimal Solution 

``` java
    public static List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
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
        for(int i=idx;i<arr.length;++i){
            if(i>idx && arr[i-1]==arr[i]) continue;
            if(arr[i]>target) break;
            temp.add(arr[i]);
            findCombinations(arr,target-arr[i],temp,res,i+1);
            temp.remove(temp.size()-1);
        }
    }
```