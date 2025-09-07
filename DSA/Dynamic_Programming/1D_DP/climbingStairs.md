# Question

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?



##### Example:

Input: n = 2

Output: 2

Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps




### Solve: [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)
   


# Optimal Solution:  


``` java
    public int climbStairs(int n) {
        int count1 = 1, count2 = 2;
        if(n==1) return count1;
        if(n==2) return count2;
        int count = count1 + count2;
        for(int i=3;i<=n;++i){
            count = count1+count2;
            count1 = count2;
            count2 = count;
        }
        return count;
    }
```
### Time Complexity: O(n)
### Space Complexity: O(1)