# Question:

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.
 

##### Example 1:

Input: nums = [2,2,1]

Output: 1

### Solve: [https://leetcode.com/problems/single-number/description/](https://leetcode.com/problems/single-number/description/)

***

# Brute Force:

``` java
public int singleNumber(int[] nums) {
    HashMap<Integer,Integer> map = new HashMap<>();
    for(int i=0;i<nums.length;++i){
        map.put(nums[i],map.getOrDefault(nums[i],0)+1);
    }
    for(Map.Entry<Integer,Integer> entry :map.entrySet()){
        if(entry.getValue()==1) 
            return entry.getKey();
    }
    return 0;
}
```

### Time Complexity: O(n) + O(n/2)
### Space Complexity: O(n/2)

# Optimal Approch:

``` java
public int singleNumber(int[] nums) {
    int xor = 0;
    for(int i: nums) xor ^= i;
    return xor;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)