# Question 

You're given a sorted array 'a' of 'n' integers and an integer 'x'.

Find the floor and ceiling of 'x' in 'a[0..n-1]'.

Note:
Floor of 'x' is the largest element in the array which is smaller than or equal to 'x'.

Ceiling of 'x' is the smallest element in the array greater than or equal to 'x'.


##### Example:
Input: 
n=6, x=5, a=[3, 4, 7, 8, 8, 10]     

*** 


# Optimal Solution  

``` java
    public static int[] getFloorAndCeil(int[] arr, int n, int x) {
      int ans[] = new int[2];
      int low=0,high=n-1;
      while(low<=high){
        int mid = low+(high-low)/2;
        if(arr[mid]<=x)
          low = mid+1;
        else
          high = mid-1;
      }
      ans[0] = high>=0?arr[high]:-1;

      low=0;
      high=n-1;
      while(low<=high){
        int mid = low+(high-low)/2;
        if(arr[mid]<x)
          low = mid+1;
        else
          high = mid-1;
      }
      ans[1] = low<n?arr[low]:-1;

      return ans;
    }
```

### Time Complexity: O(2logN)  
### Space Complexity: O(1) 