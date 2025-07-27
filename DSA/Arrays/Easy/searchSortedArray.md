# Question

Given an array, arr[] sorted in ascending order and an integer k. Return true if k is present in the array, otherwise, false.

##### Examples:

Input: arr[] = [1, 2, 3, 4, 6], k = 6

Output: true

Exlpanation: Since, 6 is present in the array at index 4 (0-based indexing), output is true.

### Solve: [https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1](https://www.geeksforgeeks.org/problems/who-will-win-1587115621/1)


***

# BruteForce Solution

``` java
static boolean searchInSorted(int arr[], int k) {
    for(int i=0;i<arr.length;++i){
        if(arr[i]==k) return true;            
    }
    return false;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)


# Optimal Solution

``` java
static boolean searchInSorted(int arr[], int k) {
    int low = 0, high = arr.length-1;
    while(low<=high){
        int mid = (low+high) /2;
        if(arr[mid]==k) return true;
        else if(arr[mid]>k) high = mid-1;
        else low = mid + 1;
    }
    return false;
}
```

### Time Complexity: O(logn)
### Space Complexity: O(1)