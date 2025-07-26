# Question 

You're given a sorted array 'a' of 'n' integers and an integer 'x'.

Find the floor and ceiling of 'x' in 'a[0..n-1]'.

Note:
Floor of 'x' is the largest element in the array which is smaller than or equal to 'x'.

Ceiling of 'x' is the smallest element in the array greater than or equal to 'x'.


##### Example:
Input: 
n=6, x=5, a=[3, 4, 7, 8, 8, 10] 

### Solve: [https://www.naukri.com/code360/problems/ceiling-in-a-sorted-array_1825401](https://www.naukri.com/code360/problems/ceiling-in-a-sorted-array_1825401)

*** 


# Optimal Solution  

``` java
    public static int[] getFloorAndCeil(int[] nums, int n, int target) {
        int arr[] = new int[2];
        int low = 0, high = n-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        arr[0] = high<0 ? -1 : nums[high];
        if(arr[0]==target)
            return new int[]{target,target};
        arr[1] = low>=n ? -1 : nums[low];
        return arr;
    }
```

### Time Complexity: O(2logN)  
### Space Complexity: O(1) 