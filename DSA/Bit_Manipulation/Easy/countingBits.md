# Question

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

##### Example:

Input: n = 2

Output: [0,1,1]

Explanation:
0 --> 0
1 --> 1
2 --> 10


### Solve: [https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)
   


# Optimal Solution:  
``` java
    public int[] countBits(int n) {
        int res[] = new int[n+1];
        for(int i=0;i<=n;++i){
            res[i] = res[i>>1] + (i&1);
        }
        return res;
    }
```
### Time Complexity: O(n+1)  
### Space Complexity: O(n+1) 