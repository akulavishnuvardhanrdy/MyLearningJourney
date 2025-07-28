# Question

Given an array arr[] containing both positive and negative integers, the task is to find the length of the longest subarray with a sum equals to 0.

Note: A subarray is a contiguous part of an array, formed by selecting one or more consecutive elements while maintaining their original order.

 
 

##### Example:

Input: arr[] = [15, -2, 2, -8, 1, 7, 10, 23]

Output: 5

Explanation: The longest subarray with sum equals to 0 is [-2, 2, -8, 1, 7].

### Solve: [https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1](https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

***

# Optimal Solution


``` java
    int maxLength(int nums[]) {
        Map<Integer,Integer> map = new HashMap<Integer,Integer>();
        int max = 0;
        map.put(0,-1);
        int sum =0;
        for(int i=0;i<nums.length;++i){
            sum+=nums[i];
            if(map.containsKey(sum)){
                max = Math.max(max,i-map.get(sum));
            }
            else{
                map.put(sum,i);
            }
        }
        return max;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)