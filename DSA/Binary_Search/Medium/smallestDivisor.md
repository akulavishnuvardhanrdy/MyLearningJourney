# Question  
Given an array of integers nums and an integer threshold, we will choose a positive integer divisor, divide all the array by it, and sum the division's result. Find the smallest divisor such that the result mentioned above is less than or equal to threshold.

Each result of the division is rounded to the nearest integer greater than or equal to that element. (For example: 7/3 = 3 and 10/2 = 5).

The test cases are generated so that there will be an answer.
 

##### Example 1:

Input: nums = [1,2,5,9], threshold = 6

Output: 5

Explanation: We can get a sum to 17 (1+2+5+9) if the divisor is 1. 
If the divisor is 4 we can get a sum of 7 (1+1+2+3) and if the divisor is 5 the sum will be 5 (1+1+1+2). 

### Solve: [https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/)

***   


# Optimal Solution*  
``` java
     public int smallestDivisor(int[] nums, int threshold) {
        int low = 1, high = maxElement(nums);
        while(low<=high){
            int mid = low+(high-low)/2;
            int getValue = findSum(nums,mid);
            if(getValue>threshold)
                low = mid+1;
            else
                high = mid-1;
        }
        return low;
    }

    int findSum(int nums[],int mid){
        int count = 0;
        for(int i:nums){
            count+=(i+mid-1)/mid;
        }
        return count;
    }

    int maxElement(int nums[]){
        int max = Integer.MIN_VALUE;
        for(int i:nums){
            if(i>max)
                max = i;
        }
        return max;
    }
```
### Time Complexity: O(N+N*log(max number))  
### Space Complexity: O(1) 