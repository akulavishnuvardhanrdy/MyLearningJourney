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
    public int sumSubarrayMins(int[] arr) {
        int left[] = new int[arr.length];
        int right[] = new int[arr.length];
        long sum = 0;
        int mod = (int)Math.pow(10,9)+7;
        Stack<int[]> st = new Stack<>();
        for(int i=0;i<arr.length;++i){
            while(!st.isEmpty() && arr[i]<st.peek()[0])
                    st.pop();
            if(st.isEmpty())
                left[i] = i+1;
            else{
                left[i] = i-st.peek()[1];
            }
            st.add(new int[]{arr[i],i});
        }
        st.clear();
        for(int i=arr.length-1;i>=0;--i){
            while(!st.isEmpty() && arr[i]<=st.peek()[0])
                st.pop();
            if(st.isEmpty())
                right[i] = arr.length-i;
            else
                right[i] = st.peek()[1] - i;
            st.add(new int[]{arr[i],i});
        }
        for(int i=0;i<arr.length;++i){
            sum+=(long)arr[i]*left[i]*right[i];
            sum%=mod;
        }
        return (int)sum;
    }
```
### Time Complexity: O(5*n)
### Space Complexity: O(3*n)