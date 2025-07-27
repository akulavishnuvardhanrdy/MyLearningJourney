# Question

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

 

##### Example 1:

Input: nums = [3,2,3]

Output: 3


### Solve: [https://leetcode.com/problems/majority-element/description/](https://leetcode.com/problems/majority-element/description/)

***

# BruteForce Solution

``` java
public int majorityElement(int[] nums) {
    int n = nums.length;
    for(int i=0;i<n;++i){
        int count=0;
        for(int j=i;j<n;++j){
            if(nums[i]==nums[j]) count++;
        }
        if(count>n/2) return nums[i];
    }
    return 0;
}
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)


# Better Solution

``` java
public int majorityElement(int[] nums) {
    HashMap<Integer,Integer> map = new HashMap<>();
    int n = nums.length;
    for(int i=0;i<n;++i){
        map.put(nums[i],map.getOrDefault(nums[i],0)+1);
    }
    for(Map.Entry<Integer,Integer> entry : map.entrySet()){
        if(entry.getValue()>n/2)
            return entry.getKey();
    }
    return 0;
}
```

### Time Complexity: O(2n)
### Space Complexity: O(n/2 )


# Optimal Solution

## Moore Voting Algorithm

``` java
public int majorityElement(int[] nums) {
    int ele = 0, count =0;
    for(int i=0;i<nums.length;++i){
        if(count==0) ele = nums[i];
        if(ele == nums[i]) count++;
        else count--;
    }
    return ele;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)