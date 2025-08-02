# Question

You are given two numbers a and b. Your task is to swap the given two numbers.

Note: Try to do it without a temporary variable

##### Example:

Input: a = 13, b = 9

Output: 9 13

Explanation: After swapping it becomes 9 and 13.


### Solve: [https://www.geeksforgeeks.org/problems/swap-two-numbers3844/1](https://www.geeksforgeeks.org/problems/swap-two-numbers3844/1)
   


# Optimal Solution:  
``` java
    static List<Integer> get(int a, int b) {
        // code here
        a = a^b;
        b = a^b;
        a = a^b;
        List<Integer> res = new ArrayList<>();
        res.add(a);
        res.add(b);
        return res;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 