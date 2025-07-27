# Question

Given an array nums, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return false.

There may be duplicates in the original array.

Note: An array A rotated by x positions results in an array B of the same length such that B[i] == A[(i+x) % A.length] for every valid index i.

 

##### Example 1:

Input: nums = [3,4,5,1,2]

Output: true

Explanation: [1,2,3,4,5] is the original sorted array.
You can rotate the array by x = 3 positions to begin on the element of value 3: [3,4,5,1,2].

### Solve: [https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/)

***

# BruteForce Solution

``` java
public boolean check(int[] nums) {
    int min = 0;
    int n = nums.length;
    for(int i=0;i<n-1;++i){
        if(nums[i]>nums[i+1]){
            min=i+1;
            break;
        }
    }
    int p = (min+1)%n;
    while(p!=min){
        int prev = p==0?n-1:p-1;
        if(nums[p]<nums[prev]) return false;
        p = (p+1)%n;
    }
    return true;
}
```

### Time Complexity: O(n)+O(n)
### Space Complexity: O(1)


# Optimal Solution

``` java
public boolean check(int[] nums) {
    int count = 0;
    int n = nums.length;
    for(int i=0;i<n;++i){
        if(nums[(i+1)%n]<nums[i]){
            count++;
        }
    }
    return count>1?false:true;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)