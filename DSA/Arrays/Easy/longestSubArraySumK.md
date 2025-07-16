# Question

Given an array arr[] containing integers and an integer k, your task is to find the length of the longest subarray where the sum of its elements is equal to the given value k. If there is no subarray with sum equal to k, return 0.

##### Examples:

Input: arr[] = [10, 5, 2, 7, 1, -10], k = 15

Output: 6

Explanation: Subarrays with sum = 15 are [5, 2, 7, 1], [10, 5] and [10, 5, 2, 7, 1, -10]. The length of the longest subarray with a sum of 15 is 6.


***

# BruteForce Solution

``` java
public int longestSubarray(int[] arr, int k) {
    int max=0;
    int n = arr.length;
    for(int i=0;i<n;++i){
        int sum=0,count=0;
        for(int j=i;j<n;++j){
            sum+=arr[j];
            count++;
            if(sum==k)
                max = Math.max(max,count);
        }
    }
    return max;
}
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)


# Optimal Solution

``` java
public int longestSubarray(int[] arr, int k) {
    int len = 0,sum=0;
    Map<Integer,Integer> map = new HashMap<>();
    map.put(0,-1);
    for(int i=0;i<arr.length;++i){
        sum+=arr[i];
        if(map.containsKey(sum-k)){
            len = Math.max(len,i-map.get(sum-k));
        }
        if(!map.containsKey(sum))
            map.put(sum,i);
    }
    return len;
}
```

### Time Complexity: O(n)
### Space Complexity: O(n)



# Optimal Solution

``` java
public static int longestSubarrayWithSumK(int []arr, long k) {
    int right=0, left=0, sum=0, maxLen=0;
    while(right<arr.length){
        sum+=arr[right];
        while(sum>k){
            sum-=arr[left];
            left++;
        }
        if(sum==k){
            maxLen=Math.max(maxLen,right-left+1);
        }
        right++;
    }
    return maxLen;
}
```

### Time Complexity: O(2n)
### Space Complexity: O(1)