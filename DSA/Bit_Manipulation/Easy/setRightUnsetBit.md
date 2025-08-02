# Question

Given a non-negative number n . The problem is to set the rightmost unset bit in the binary representation of n.


##### Example:

Input: n = 6

Output: 7

Explanation: The binary representation of 6 is 110. After setting right most bit it becomes 111 which is 7.


### Solve: [https://www.geeksforgeeks.org/problems/set-the-rightmost-unset-bit4436/1](https://www.geeksforgeeks.org/problems/set-the-rightmost-unset-bit4436/1)
   


# Optimal Solution:  
``` java
    static int setBit(int n) {
        return n|n+1;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 