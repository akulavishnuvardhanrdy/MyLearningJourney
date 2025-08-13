# Question

You are given an array of integers nums, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.



##### Example:

Input: nums = [1,3,-1,-3,5,3,6,7], k = 3

Output: [3,3,5,5,6,7]

Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7



### Solve: [https://leetcode.com/problems/sliding-window-maximum/](https://leetcode.com/problems/sliding-window-maximum/)
   


# Optimal Solution:  


``` java
    public int[] maxSlidingWindow(int[] nums, int k) {
        int res[] = new int[nums.length-k+1];
        ArrayDeque<int[]> dq = new ArrayDeque<>();
        int rmvIdx = k-1;
        for(int i=0;i<rmvIdx;++i){
            while(!dq.isEmpty() && nums[i]>dq.peekLast()[1])
                dq.pollLast();
            dq.addLast(new int[]{i,nums[i]});
        }
        for(int i=rmvIdx;i<nums.length;++i){
            while(!dq.isEmpty() && nums[i]>dq.peekLast()[1])
                dq.pollLast();
            dq.addLast(new int[]{i,nums[i]});
            res[i-rmvIdx] = dq.peekFirst()[1];
            if(dq.peekFirst()[0]==i-rmvIdx)
                dq.pollFirst();
        }
        return res;
    }
```
### Time Complexity: O(2*n)
### Space Complexity: O(k)