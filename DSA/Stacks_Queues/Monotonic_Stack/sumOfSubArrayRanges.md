# Question

You are given an integer array nums. The range of a subarray of nums is the difference between the largest and smallest element in the subarray.

Return the sum of all subarray ranges of nums.

A subarray is a contiguous non-empty sequence of elements within an array.


##### Example:

Input: nums = [1,2,3]

Output: 4

Explanation: The 6 subarrays of nums are the following:
[1], range = largest - smallest = 1 - 1 = 0 
[2], range = 2 - 2 = 0
[3], range = 3 - 3 = 0
[1,2], range = 2 - 1 = 1
[2,3], range = 3 - 2 = 1
[1,2,3], range = 3 - 1 = 2
So the sum of all ranges is 0 + 0 + 0 + 1 + 1 + 2 = 4.



### Solve: [https://leetcode.com/problems/sum-of-subarray-ranges/description/](https://leetcode.com/problems/sum-of-subarray-ranges/description/)
   


# Optimal Solution:  


``` java
    public long subArrayRanges(int[] nums) {
        return subArrayMaximums(nums)-subArrayMinimums(nums);
    }
    long subArrayMinimums(int nums[]){
        int left[] = new int[nums.length];
        int right[] = new int[nums.length];
        ArrayDeque<int[]> st = new ArrayDeque<>();
        long res = 0;
        for(int i=0; i<nums.length;++i){
            while(!st.isEmpty() && nums[i]<st.peek()[0])
                st.pop();
            if(st.isEmpty())
                left[i] = i+1;
            else
                left[i] = i-st.peek()[1];
            st.push(new int[]{nums[i],i});
        }
        st.clear();
        for(int i=nums.length-1; i>=0; --i){
            while(!st.isEmpty() && nums[i]<=st.peek()[0])
                st.pop();
            if(st.isEmpty())
                right[i] = nums.length-i;
            else
                right[i] = st.peek()[1]-i;
            st.push(new int[]{nums[i],i});
        }
        for(int i=0;i<nums.length;++i){
            res+=(long)nums[i]*left[i]*right[i];
        }
        return res;
    }
    long subArrayMaximums(int nums[]){
        int left[] = new int[nums.length];
        int right[] = new int[nums.length];
        ArrayDeque<int[]> st = new ArrayDeque<>();
        long res = 0;
        for(int i=0; i<nums.length;++i){
            while(!st.isEmpty() && nums[i]>st.peek()[0])
                st.pop();
            if(st.isEmpty())
                left[i] = i+1;
            else
                left[i] = i-st.peek()[1];
            st.push(new int[]{nums[i],i});
        }
        st.clear();
        for(int i=nums.length-1; i>=0; --i){
            while(!st.isEmpty() && nums[i]>=st.peek()[0])
                st.pop();
            if(st.isEmpty())
                right[i] = nums.length-i;
            else
                right[i] = st.peek()[1]-i;
            st.push(new int[]{nums[i],i});
        }
        for(int i=0;i<nums.length;++i){
            res+=(long)nums[i]*left[i]*right[i];
        }
        return res;
    }
```
### Time Complexity: O(10*n)
### Space Complexity: O(6*n)