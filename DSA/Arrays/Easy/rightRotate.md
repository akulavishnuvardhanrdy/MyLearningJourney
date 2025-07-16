# Question

Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

 

##### Example 1:

Input: nums = [1,2,3,4,5,6,7], k = 3

Output: [5,6,7,1,2,3,4]

Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]



***

# BruteForce Solution

``` java
public void rotate(int[] nums, int k) {
    int n = nums.length;
    k=k%n;
    int arr[] = new int[n-k];
    for(int i=0;i<n-k;++i){
        arr[i] = nums[i];
    }
    int idx =0;
    for(int i=n-k;i<n;++i){
        nums[idx] = nums[i];
        idx++;
    }
    for(int i=0;i<arr.length;++i){
        nums[idx] = arr[i];
        idx++;
    }
}
```

### Time Complexity: O(n)+O(n)
### Space Complexity: O(n)


# Optimal Solution

``` java
public void rotate(int[] nums, int k) {
    int n = nums.length;
    k= k%n;
    reverse(nums,0,n-k-1);
    reverse(nums,n-k,n-1);
    reverse(nums,0,n-1);
}
void reverse(int nums[], int i, int j){
    while(i<j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
        i++;
        j--;
    }
}
```

### Time Complexity: O(n/2)+O(n/2)
### Space Complexity: O(1)