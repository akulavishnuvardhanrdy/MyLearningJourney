# Question
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

 

##### Example 1:

Input: nums = [1,3,5,6], target = 5

Output: 2

### Solve: [https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/)

***

# Optimal Solution

``` java
    public int searchInsert(int[] arr, int target) {
        int low =0, high = arr.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(arr[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        if(high>=0 && arr[high]==target)
            return high;
        return low;
    }
```


### Time Complexity: O(logN)  
### Space Complexity: O(1) 