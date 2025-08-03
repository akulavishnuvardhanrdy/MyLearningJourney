# Question

Given an integer i. Print the maximum number of nodes on level i of a binary tree.

Note: The level of a binary tree starts with 1 (i.e., level 1 contains the root of the tree, level 2 contains the children of the root, and so on).

##### Example:

Input: 5

Output: 16

Explanation: The maximum number of nodes at level 5 is 16.

### Solve: [https://www.geeksforgeeks.org/problems/introduction-to-trees/1](https://www.geeksforgeeks.org/problems/introduction-to-trees/1)
   


# Optimal Solution:  
``` java
    static int countNodes(int i) {
        // code here
        return (int)Math.pow(2,i-1);
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 