# Question

Given an array of positive integers arr[] and a value sum, determine if there is a subset of arr[] with sum equal to given sum. 




##### Example:

Input: arr[] = [3, 34, 4, 12, 5, 2], sum = 9

Output: true 

Explanation: Here there exists a subset with target sum = 9, 4+3+2 = 9.



### Solve: [https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1](https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1)
   


# Optimal Solution:  
``` java
    static Boolean isSubsetSum(int arr[], int sum) {
        // code here
        return isPresent(arr,sum,0,0);
    }
    static Boolean isPresent(int nums[], int target, int idx, int sum){
        if(sum>target)
            return false;
        if(idx==nums.length){
            if(sum==target)
                return true;
            return false;
        }
        if(isPresent(nums,target,idx+1,sum+nums[idx])==true) 
            return true;
        if(isPresent(nums,target,idx+1,sum)==true) 
            return true;
        return false;
    }
```
### Time Complexity: O(2^n)  
### Space Complexity: O(n) 