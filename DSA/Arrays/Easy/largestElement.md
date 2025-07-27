# Question:

Given an array arr[]. The task is to find the largest element and return it.

##### Examples:

Input: arr[] = [1, 8, 7, 56, 90]

Output: 90

Explanation: The largest element of the given array is 90.


### Solve[https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1](https://www.geeksforgeeks.org/problems/largest-element-in-array4009/1)

***

# Brute Force:

``` java
    public static int largest(int[] arr) {            
        Arrays.sort(arr);
        return arr[arr.length-1];        
    }
```

### Time Complexity: O(n* logn)
### Space Complexity: O(1)

# Optimal Approch:

``` java
    public static int largest(int[] arr) {
        int max=arr[0];
        for(int i=0;i<arr.length;++i){
            if(arr[i]>max) max = arr[i];
        }
        return max;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)