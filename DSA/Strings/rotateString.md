# Question

Given two strings s and goal, return true if and only if s can become goal after some number of shifts on s.

A shift on s consists of moving the leftmost character of s to the rightmost position.

For example, if s = "abcde", then it will be "bcdea" after one shift.
 



##### Example:

Input: s = "abcde", goal = "cdeab"

Output: true



### Solve: [https://leetcode.com/problems/rotate-string](https://leetcode.com/problems/rotate-string)

***

# Optimal Solution
        

``` java
    public boolean rotateString(String s, String goal) {
        if(s.length()!=goal.length())
            return false;
        return (s+s).contains(goal);
    }
```

### Time Complexity: O(2n) 
### Space Complexity: O(2n)