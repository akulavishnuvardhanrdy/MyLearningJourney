# Question

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.



##### Example:

Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]

Output: 6

Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.



### Solve: [https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)
   


# Optimal Solution:  


``` java
    public int trap(int[] arr) {
        int left = 0, right = arr.length-1;
        int lMax = -1,rMax = -1;
        int res = 0;
        while(left<right){
            if(arr[left]<arr[right]){
                if(arr[left]>=lMax)
                    lMax = arr[left];
                else
                    res+=lMax-arr[left];
                left++;
            }
            else{
                if(arr[right]>=rMax)
                    rMax = arr[right];
                else
                    res+=rMax-arr[right];
                right--;
            }
        } 
        return res;
    }
```
### Time Complexity: O(n)
### Space Complexity: O(1)