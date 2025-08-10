# Question

Given an integer array arr. For each element in the array, check whether the right adjacent element (on the next immediate position) of the array is smaller. If the next element is smaller, update the current index to that element. If not, then update to -1.

Note: Update the array in itself.



##### Example:

Input: arr[] = [4, 2, 1, 5, 3]

Output: [2, 1, -1, 3, -1]

Explanation: Array elements are 4, 2, 1, 5, 3. Next to 4 is 2 which is smaller, so we print 2. Next of 2 is 1 which is smaller,so we print 1. Next of 1 is 5 which is greater, so we print -1. Next of 5 is 3 which is smaller, so we print 3.  Note that for last element, output is always  going to be -1 because there is no element on right.



### Solve: [https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1](https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1)
   


# Optimal Solution:  


``` java
    public void immediateSmaller(int nums[]) {
        // code here
        for(int i=0;i<nums.length-1;++i){
            if(nums[i]>nums[i+1])
                nums[i] = nums[i+1];
            else
                nums[i] = -1;
        }
        nums[nums.length-1] = -1;
    }
```
### Time Complexity: O(n)
### Space Complexity: O(1)