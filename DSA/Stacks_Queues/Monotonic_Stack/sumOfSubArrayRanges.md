# Question

Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. Since the answer may be large, return the answer modulo 109 + 7.



##### Example:

Input: arr = [3,1,2,4]

Output: 17

Explanation: 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17.



### Solve: [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)
   


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