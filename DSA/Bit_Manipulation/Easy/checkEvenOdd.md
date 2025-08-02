# Question

Given a positive integer n, determine whether it is odd or even. Return true if the number is even and false if the number is odd. 

##### Example:

Input: n = 15

Output: false

Explanation: The number is not divisible by 2, Odd number.

### Solve: [https://www.geeksforgeeks.org/problems/odd-or-even3618/1](https://www.geeksforgeeks.org/problems/odd-or-even3618/1)
   


# Optimal Solution:  
``` java
    static boolean isEven(int n) {
        return (n & 1)==0 ? true : false;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 