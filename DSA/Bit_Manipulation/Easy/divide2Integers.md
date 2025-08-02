# Question

Given two integers dividend and divisor, divide two integers without using multiplication, division, and mod operator.

The integer division should truncate toward zero, which means losing its fractional part. For example, 8.345 would be truncated to 8, and -2.7335 would be truncated to -2.

Return the quotient after dividing dividend by divisor.

Note: Assume we are dealing with an environment that could only store integers within the 32-bit signed integer range: [−231, 231 − 1]. For this problem, if the quotient is strictly greater than 231 - 1, then return 231 - 1, and if the quotient is strictly less than -231, then return -231.


##### Example:

Input: dividend = 10, divisor = 3

Output: 3

Explanation: 10/3 = 3.33333.. which is truncated to 3.


### Solve: [https://leetcode.com/problems/divide-two-integers/description/](https://leetcode.com/problems/divide-two-integers/description/)
   


# Optimal Solution:  
``` java
    public int divide(int dividend, int divisor) {
        if(dividend==Integer.MIN_VALUE){
            if(divisor==-1)
                return Integer.MAX_VALUE;
            if(divisor==1)
                return Integer.MIN_VALUE;
        }
        boolean neg = (dividend<0)^(divisor<0);
        long ldividend = Math.abs((long)dividend);
        long ldivisor = Math.abs((long)divisor);
        int count = 0;
        for(int i=31;i>=0;--i){
            if((ldivisor<<i)<=ldividend){
                ldividend -= (ldivisor<<i);
                count += 1<<i;
            }
        }
        return neg?count*-1:count;
    }
```
### Time Complexity: O(N), where N = dividend / divisor.  
### Space Complexity: O(1) 