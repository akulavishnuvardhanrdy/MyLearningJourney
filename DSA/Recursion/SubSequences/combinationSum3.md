# Question  

Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.



##### Examples :

Input: k = 3, n = 7

Output: [[1,2,4]]

Explanation:

1 + 2 + 4 = 7

There are no other valid combinations.



### Solve: [https://leetcode.com/problems/combination-sum-iii/](https://leetcode.com/problems/combination-sum-iii/)

*** 

# Optimal Solution 

``` java
    public List<List<Integer>> combinationSum3(int k, int n) {
        int arr[] = new int[]{1,2,3,4,5,6,7,8,9};
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        findCombinations(arr,res,curr,k,n,0,0);
        return res;
    }
    void findCombinations(int arr[],List<List<Integer>> res,List<Integer> curr,int len,int target,int idx,int currlen){
        if(currlen==len || idx==arr.length){
            if(currlen==len && target==0){
                res.add(new ArrayList<>(curr));
            }
            return ;
        }
        curr.add(arr[idx]);
        findCombinations(arr,res,curr,len,target-arr[idx],idx+1,currlen+1);
        curr.remove(curr.size()-1);
        findCombinations(arr,res,curr,len,target,idx+1,currlen);
    }
```