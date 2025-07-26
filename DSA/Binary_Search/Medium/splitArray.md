# Question  
Given an integer array nums and an integer k, split nums into k non-empty subarrays such that the largest sum of any subarray is minimized.

Return the minimized largest sum of the split.

A subarray is a contiguous part of the array.
 

##### Example 1:

Input: nums = [7,2,5,10,8], k = 2

Output: 18

Explanation: There are four ways to split nums into two subarrays.
The best way is to split it into [7,2,5] and [10,8], where the largest sum among the two subarrays is only 18.

### Solve: [https://leetcode.com/problems/split-array-largest-sum/description/](https://leetcode.com/problems/split-array-largest-sum/description/)

***   


# Optimal Solution*  
``` java
    public int splitArray(int[] nums, int k) {
        int temp[] = MaxTotal(nums);
        int low = temp[0],high = temp[1];
        while(low<=high){
            int mid = low+(high-low)/2;
            if(isPossible(nums,k,mid)){
                high = mid-1;
            }
            else
                low = mid+1;
        }
        return low;
    }

    public boolean isPossible(int nums[],int k, int mid){
        int count=1;
        int currSum =0;
        for(int i:nums){
            if(currSum+i>mid){
                count++;
                currSum = i;
                if(count>k) return false;
            }
            else
                currSum+=i;
        }
        return true;
    }

    public int[] MaxTotal(int nums[]){
        int max = Integer.MIN_VALUE;
        int sum =0;
        for(int i:nums){
            sum+=i;
            if(i>max)
                max = i;
        }
        return new int[]{max,sum};
    }
```
### Time Complexity: O(N+N*log(sumElements-maxElement))  
### Space Complexity: O(1) 