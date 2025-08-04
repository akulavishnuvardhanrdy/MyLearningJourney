# Question

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

##### Example:

Input: root = [3,9,20,null,null,15,7]

Output: 3


### Solve: [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
   


# Optimal Solution:  
``` java
    public int maxDepth(TreeNode root) {
        if(root==null)
            return 0;
        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);
        return 1+Math.max(lh,rh);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1) 