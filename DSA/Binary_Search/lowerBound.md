# Question  
Given a sorted array arr[] and an integer x, find the index (0-based) of the largest element in arr[] that is less than or equal to x. This element is called the floor of x. If such an element does not exist, return -1.

Note: In case of multiple occurrences of ceil of x, return the index of the last occurrence.

##### Examples

Input: arr[] = [1, 2, 8, 10, 10, 12, 19], x = 5

Output: 1

Explanation: Largest number less than or equal to 5 is 2, whose index is 1.
  

***

# Optimal Solution  

``` java
    static int findFloor(int[] arr, int x) {
        // write code here
        int low = 0, high = arr.length-1;
        int ans = -1;
        while(low<=high){
            int mid=low+(high-low)/2;
            if(arr[mid]<=x) {
                ans = mid;
                low=mid+1;
            }
            else
                high=mid-1;
        }
        return ans;
    }
```

### Time Complexity: O(logN)  
### Space Complexity: O(1) 