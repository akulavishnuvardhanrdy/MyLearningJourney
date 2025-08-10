# Question

Given a rows x cols binary matrix filled with 0's and 1's, find the largest rectangle containing only 1's and return its area.


##### Example:

Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]

Output: 6

Explanation: The maximal rectangle is shown in the above picture.


### Solve: [https://leetcode.com/problems/maximal-rectangle/](https://leetcode.com/problems/maximal-rectangle/)
   


# Optimal Solution:  


``` java
    public int maximalRectangle(char[][] matrix) {
        int n = matrix.length;
        int m = matrix[0].length;
        int preSum[][] = new int[n][m];
        int maxArea = -1;
        for(int i=0;i<n;++i){
            for(int j=0;j<m;++j){
                int val = matrix[i][j]-'0';
                if(i==0)
                    preSum[i][j] = val;
                else if(val==1)
                    preSum[i][j]+=(preSum[i-1][j]+1);
                else
                    preSum[i][j] = 0;
            }
        }
        for(int i=0;i<n;++i){
            maxArea = Math.max(maxArea,largestRectangleArea(preSum[i]));
        }
        return maxArea;
    }

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
### Time Complexity: O(n*m)+O(m*n)
### Space Complexity: O(m*n)