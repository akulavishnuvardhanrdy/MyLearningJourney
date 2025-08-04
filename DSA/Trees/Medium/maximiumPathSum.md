# Question

A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any non-empty path.

 

##### Example:

Input: root = [1,2,3]

Output: 6

Explanation: The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.


### Solve: [https://leetcode.com/problems/binary-tree-maximum-path-sum/description/](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)
   


# Optimal Solution:  
``` java
    int max =Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        findSum(root);
        return max;
    }
    int findSum(TreeNode root){
        if(root == null)
            return 0;
        int lsum = findSum(root.left);
        int rsum = findSum(root.right);
        lsum = lsum>0?lsum:0;
        rsum = rsum>0?rsum:0;
        max = Math.max(max,lsum+rsum+root.val);
        return root.val+Math.max(lsum,rsum);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N)   