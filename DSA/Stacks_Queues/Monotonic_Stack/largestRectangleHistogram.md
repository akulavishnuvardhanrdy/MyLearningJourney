# Question

Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.


##### Example:

Input: heights = [2,1,5,6,2,3]

Output: 10

Explanation: The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.


### Solve: [https://leetcode.com/problems/largest-rectangle-in-histogram/](https://leetcode.com/problems/largest-rectangle-in-histogram/)
   


# Optimal Solution:  


``` java
    public int largestRectangleArea(int[] nums) {
        int right[] = new int[nums.length];
        int left[] = new int[nums.length];
        ArrayDeque<int[]> st = new ArrayDeque<>();
        int maxArea = -1;
        for(int i=nums.length-1;i>=0;i--){
            while(!st.isEmpty() && st.peekLast()[0]>=nums[i])
                st.pollLast();
            if(st.isEmpty()){
                right[i] = nums.length;
            }
            else{
                right[i] = st.peekLast()[1];
            }
            st.addLast(new int[]{nums[i],i});
        }
        st.clear();
        for(int i=0;i<nums.length;++i){
            while(!st.isEmpty() && st.peekLast()[0]>=nums[i])
                st.pollLast();
            if(st.isEmpty()){
                left[i] = -1;
            }
            else{
                left[i] = st.peekLast()[1];
            }
            st.addLast(new int[]{nums[i],i});
        }
        for(int i=0;i<nums.length;++i){
            int area = nums[i]*(right[i]-left[i]-1);
            maxArea = Math.max(area,maxArea);
        }
        return maxArea;
    }
```
### Time Complexity: O(5*n)
### Space Complexity: O(2n)