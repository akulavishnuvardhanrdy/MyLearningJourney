# Question 
Given an increasing sorted rotated array arr of distinct integers. The array is right-rotated k times. Find the value of k.

Let's suppose we have an array arr = [2, 4, 6, 9], so if we rotate it by 2 times so that it will look like this:

After 1st Rotation : [9, 2, 4, 6]

After 2nd Rotation : [6, 9, 2, 4]

##### Examples:

Input: arr = [5, 1, 2, 3, 4]

Output: 1

Explanation: The given array is 5 1 2 3 4. The original sorted array is 1 2 3 4 5. We can see that the array was rotated 1 times to the right    

***   


# Optimal Solution  
``` java
    public int findKRotation(List<Integer> arr) {
        int min=Integer.MAX_VALUE,minIndex=0;
        int low=0,high=arr.size()-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(arr.get(low)<=arr.get(mid)){
                min = Math.min(arr.get(low),min);
                minIndex = min==arr.get(low) ? low : minIndex;
                low = mid+1;
            }
            else{
                min = Math.min(arr.get(mid),min);
                minIndex = min==arr.get(mid) ? mid : minIndex;
                high = mid-1;
            }
        }
        return minIndex;
    }
```
### Time Complexity: O(logN)  
### Space Complexity: O(1) 