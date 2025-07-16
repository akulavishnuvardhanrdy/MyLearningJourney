# Question

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

 

##### Example 1:

Input: nums = [1,1,2]

Output: 2, nums = [1,2,_]

Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).


***

# BruteForce Solution

``` java
public int removeDuplicates(int[] nums) {
    Set<Integer> hs = new LinkedHashSet<>();
    for(int num: nums){
        hs.add(num);
    }
    int i=0;
    for(int val: hs){
        nums[i++] = val;
    }
    return hs.size();
}
```

### Time Complexity: O(n)+O(n)
### Space Complexity: O(n)


# Optimal Solution

``` java
public int removeDuplicates(int[] nums) {
    int pnt1 = 0, pnt2 = 0;
    while(pnt2!=nums.length){
        if(nums[pnt1]==nums[pnt2]){
            pnt2++;
        }
        else{
            nums[pnt1+1] = nums[pnt2];
            pnt1++;
            pnt2++;
        }
    }
    return pnt1+1;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)