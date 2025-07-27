# Question

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

 

##### Example 1:

Input: nums = [0,1,0,3,12]

Output: [1,3,12,0,0]

### Solve: [https://leetcode.com/problems/move-zeroes/description/](https://leetcode.com/problems/move-zeroes/description/)

***

# BruteForce Solution

``` java
public void moveZeroes(int[] nums) {
    int arr[] = new int[nums.length];
    int idx=0;
    for(int i : nums){
        if(i!=0) arr[idx++] = i;
    }
    for(int i=0;i<idx;++i){
        nums[i] = arr[i];
    }
    for(int i=idx;i<nums.length;++i){
        nums[i] = 0;
    }
}
```

### Time Complexity: O(n)+O(n)
### Space Complexity: O(n)


# Optimal Solution

``` java
public void moveZeroes(int[] nums) {
    int pnt1 = 0, pnt2 = 0;
    while(pnt2<nums.length){
        if(nums[pnt2]!=0){
            nums[pnt1] = nums[pnt2];
            if(pnt1!=pnt2) nums[pnt2] = 0;
            pnt1++;
        }
        pnt2++;
    }
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)