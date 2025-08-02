# Question

Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

##### Example:

Input: n = 1

Output: true

Explanation: 20 = 1

### Solve: [https://leetcode.com/problems/power-of-two/description/](https://leetcode.com/problems/power-of-two/description/)
   


# Optimal Solution:  
``` java
    public boolean isPowerOfTwo(int n) {
        if(n<=0) return false;
        return (n&n-1)==0?true:false;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 