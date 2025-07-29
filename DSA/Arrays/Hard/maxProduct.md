# Question

Given an integer array nums, find a subarray that has the largest product, and return the product.

The test cases are generated so that the answer will fit in a 32-bit integer.
 

##### Example:

Input: nums = [2,3,-2,4]

Output: 6

Explanation: [2,3] has the largest product 6.

### Solve: [https://leetcode.com/problems/maximum-product-subarray/](https://leetcode.com/problems/maximum-product-subarray/)

***

# Optimal Solution


``` java
    public int maxProduct(int[] nums) {
        if(nums.length==1) return nums[0];
        int n = nums.length;
        int pref[] = new int[n];
        int suff[] = new int[n];
        int prod=1;
        int max = Integer.MIN_VALUE;
        for(int i=0;i<n;++i){
            max = Math.max(max,nums[i]);
            prod*=nums[i];
            pref[i]=prod;
            if(prod==0) prod =1;
        }
        prod = 1;
        for(int j=n-1;j>=0;--j){
            prod*=nums[j];
            suff[j]=prod;
            if(prod==0) prod =1;
        }
        int maxProd = Integer.MIN_VALUE;
        for(int i=0;i<n;++i){
            maxProd=Math.max(Math.max(maxProd,pref[i]),suff[i]);
        }
        if(maxProd<max)
            return max;
        return maxProd;
    }
```

### Time Complexity: O(3n)
### Space Complexity: O(2n)