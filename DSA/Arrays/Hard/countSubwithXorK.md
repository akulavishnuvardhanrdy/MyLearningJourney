# Question

Given an array of integers arr[] and a number k, count the number of subarrays having XOR of their elements as k.

 
 

##### Example:

Input: arr[] = [4, 2, 2, 6, 4], k = 6

Output: 4

Explanation: The subarrays having XOR of their elements as 6 are [4, 2], [4, 2, 2, 6, 4], [2, 2, 6], and [6]. Hence, the answer is 4.

### Solve: [https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1](https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1)

***

# Optimal Solution


``` java
    public long subarrayXor(int arr[], int k) {
        // code here
        Map<Integer,Integer> map = new HashMap<>();
        int count =0;
        int xor =0;
        for(int i=0;i<arr.length;++i){
            xor^=arr[i];
            if(xor==k) count++;
            if(map.containsKey(xor^k)){
                count+=map.get(xor^k);
            }
            map.put(xor,map.getOrDefault(xor,0)+1);
        }
        return count;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)