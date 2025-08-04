# Question

Given a binary tree, determine if it is height-balanced.

##### Example:

Input: root = [3,9,20,null,null,15,7]

Output: true


### Solve: [https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)
   


# Optimal Solution:  
``` java
    public boolean isBalanced(TreeNode root) {
        return func(root)==-1?false:true;
    }
    int func(TreeNode root){
        if(root==null)
            return 0;
        int lh = func(root.left);
        if(lh==-1) return -1;
        int rh = func(root.right);
        if(rh==-1) return -1;
        if(Math.abs(lh-rh)>1) return -1;
        return 1+Math.max(lh,rh);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 