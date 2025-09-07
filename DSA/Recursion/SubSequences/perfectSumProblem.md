# Question

Given an array arr of non-negative integers and an integer target, the task is to count all subsets of the array whose sum is equal to the given target.

##### Example:

Input: arr[] = [5, 2, 3, 10, 6, 8], target = 10

Output: 3

Explanation: The subsets {5, 2, 3}, {2, 8}, and {10} sum up to the target 10.


### Solve: [https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1](https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1)
   


# Reccursive Solution(TLE):  
``` java
    public int perfectSum(int[] nums, int target) {
        // code here
        return count(nums,target,0,0);
    }
    int count(int nums[], int target, int idx, int sum){
        if(sum>target)
            return 0;
        if(idx==nums.length){
            if(sum==target)
                return 1;
            return 0;
        }
        int left = count(nums,target,idx+1,sum+nums[idx]);
        int right = count(nums,target,idx+1,sum);
        return left+right;
    }
```
### Time Complexity: O(2^n)  
### Space Complexity: O(n) 


# Optimal Solution(DP):  
``` java
    public static String betterString(String s1, String s2) {
        // Code here
        int n1 = s1.length();
        int n2 = s2.length();
        int res1[] = new int[n1+1];
        int res2[] = new int[n2+1];
        findDistinct(s1,res1);
        findDistinct(s2,res2);
        
        if(res1[n1]<res2[n2])
            return s2;
        return s1;
    }
    
    static void findDistinct(String s,int res[]){
        res[0] = 1;
        int last[] = new int[256];
        Arrays.fill(last,-1);
        
        for(int i=0;i<s.length();++i){
            char c = s.charAt(i);
            int sub = 0;
            if(last[c]!=-1){
                sub = res[last[c]];
            }
            res[i+1] = (2*res[i])-sub;
            last[c] = i;
        }
    }
```
### Time Complexity: O(n)  
### Space Complexity: O(n) 