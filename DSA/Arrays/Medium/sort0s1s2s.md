# Question

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

 

##### Example:

Input: nums = [2,0,2,1,1,0]

Output: [0,0,1,1,2,2]

***

# BruteForce Solution

``` java
public void sortColors(int[] nums) {
    Arrays.sort(nums); 
}
```

### Time Complexity: O(n* log n)
### Space Complexity: O(1)


# Better Solution

``` java
public void sortColors(int[] nums) {
    int ones = 0, zeros = 0, twos = 0;
    for(int i: nums){
        if(i==1)    ones++;
        else if(i==0)   zeros++;
        else    twos++;
    }
    int pnt =0;
    while(zeros-- >0) nums[pnt++] = 0;
    while(ones-- >0) nums[pnt++] = 1;
    while(twos-- >0) nums[pnt++] = 2;        
}
```

### Time Complexity: O(2n)
### Space Complexity: O(1)


# Optimal Solution

## Dutch National Flag Algoritm

``` java
public void sortColors(int[] nums) {
    int mid =0, low = 0, high =nums.length-1;
    while(mid<=high){
        if(nums[mid]==2){
            swap(nums,mid,high);
            high--;
        }
        else if(nums[mid]==0){
            swap(nums,low,mid);
            low++;
            mid++;
        }else{
            mid++;
        }
    }
}
public void swap(int[] nums,int pnt1,int pnt2){
    int temp = nums[pnt1];
    nums[pnt1] = nums[pnt2];
    nums[pnt2] = temp;
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)