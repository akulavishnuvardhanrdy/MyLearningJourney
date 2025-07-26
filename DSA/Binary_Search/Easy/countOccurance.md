# Question 
Given a sorted array, arr[] and a number target, you need to find the number of occurrences of target in arr[]. 

##### Examples :

Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 2

Output: 4

Explanation: target = 2 occurs 4 times in the given array so the output is 4.


### Solve [https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1](https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1)
*** 


# Optimal Solution 

``` java
    int countFreq(int[] nums, int target) {
        int low = 0, high = nums.length-1;
        int ans[] = new int[2];
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<target)
                low = mid+1;
            else
                high = mid-1;
        }
        if(low>=nums.length || nums[low]!=target) 
            return 0;
        ans[0] = low;

        low = 0;
        high = nums.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(nums[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        ans[1] = high;

        return ans[1]-ans[0]+1;
    }

```

### Time Complexity: O(2logN)  
### Space Complexity: O(1) 