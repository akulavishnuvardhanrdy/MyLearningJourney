# Question  
Given a sorted array arr[] and a number target, the task is to find the upper bound of the target in this given array.
The upper bound of a number is defined as the smallest index in the sorted array where the element is greater than the given number.

Note: If all the elements in the given array are smaller than or equal to the target, the upper bound will be the length of the array.

##### Examples :

Input:  arr[] = [2, 3, 7, 10, 11, 11, 25], target = 9

Output: 3

Explanation: 3 is the smallest index in arr[], at which element (arr[3] = 10) is larger than 9.

*** 

# Optimal Solution 

``` java
    int upperBound(int[] arr, int target) {
        int low = 0,high = arr.length-1;
        int ans = arr.length;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(arr[mid]>target){
                ans = mid;
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return ans;
    }
```

### Time Complexity: O(logN)  
### Space Complexity: O(1) 