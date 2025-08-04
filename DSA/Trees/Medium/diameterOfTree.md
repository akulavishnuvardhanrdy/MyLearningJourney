# Question

Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.



##### Example:

Input: root = [1,2,3,4,5]

Output: 3

Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].


### Solve: [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)
   


# Optimal Solution:  
``` java
    int max = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        func(root);
        return max;
    }
    int func(TreeNode root){
        if(root==null)
            return 0;
        int lh = func(root.left);
        int rh = func(root.right);
        max = Math.max(max,lh+rh);
        return 1+Math.max(lh,rh);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 