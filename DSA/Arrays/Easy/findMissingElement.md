# Question

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

 

##### Example 1:

Input: nums = [3,0,1]

Output: 2

Explanation:
n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

### Solve: [https://leetcode.com/problems/missing-number/submissions/1713603993/](https://leetcode.com/problems/missing-number/submissions/1713603993/)


***

# Optimal Solution

``` java
public int missingNumber(int[] nums) {
    int n = nums.length;
    int sum = 0;
    for(int i:nums) sum+=i;
    int original = (n*(n+1))/2;
    return original - sum;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)


# Optimal Solution

``` java
public int missingNumber(int[] nums) {
    int xor = 0;
    for(int i=0;i<nums.length;++i){
        xor = xor ^ nums[i];
        xor = xor ^ (i+1);
    }
    return xor;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)