# Question

Given a circular integer array nums (i.e., the next element of nums[nums.length - 1] is nums[0]), return the next greater number for every element in nums.

The next greater number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return -1 for this number.




##### Example:

Input: nums = [1,2,1]

Output: [2,-1,2]

Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number. 
The second 1's next greater number needs to search circularly, which is also 2.



### Solve: [https://leetcode.com/problems/next-greater-element-ii/](https://leetcode.com/problems/next-greater-element-ii/)
   


# Optimal Solution:  


``` java
    public int[] nextGreaterElements(int[] nums) {
        Stack<Integer> st = new Stack<>();
        int res[] = new int[nums.length];
        for(int i=nums.length-1;i>=0;--i){
            while(!st.isEmpty() && nums[i]>st.peek())
                st.pop();
            st.add(nums[i]);
        }
        for(int i=nums.length-1;i>=0;--i){
            while(!st.isEmpty()){
                if(nums[i]>=st.peek()){
                    st.pop();
                }
                else{
                    res[i] = st.peek();
                    st.add(nums[i]);
                    break;
                }
            }
            if(st.isEmpty()){
                res[i] = -1;
                st.add(nums[i]);
            }
        }
        return res;
    }
```
### Time Complexity: O(2n+2n)
### Space Complexity: O(2n+n)