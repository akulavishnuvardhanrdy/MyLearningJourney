# Question

The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.

You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.

For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.

Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.





##### Example:

Input: nums1 = [4,1,2], nums2 = [1,3,4,2]

Output: [-1,3,-1]

Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.



### Solve: [https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)
   


# Optimal Solution:  


``` java
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Stack<Integer> st = new Stack<>();
        int res[] = new int[nums1.length];
        Map<Integer,Integer> map = new HashMap<>();
        for(int i=nums2.length-1;i>=0;--i){
            while(!st.isEmpty()){
                if(nums2[i]<st.peek()){
                    map.put(nums2[i],st.peek());
                    st.add(nums2[i]);
                    break;
                }
                else 
                    st.pop();
            }
            if(st.isEmpty()){
                map.put(nums2[i],-1);
                st.add(nums2[i]);
            }
        }
        for(int i=0;i<nums1.length;++i){
            res[i] = map.get(nums1[i]);
        }
        return res;
    }
```
### Time Complexity: O(n1+n2)
### Space Complexity: O(n1+n2+n2)