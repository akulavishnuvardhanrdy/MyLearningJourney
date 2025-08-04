# Question

Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

##### Example:

Input: p = [1,2,3], q = [1,2,3]

Output: true


### Solve: [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)
   


# Optimal Solution:  
``` java
    public boolean isSameTree(TreeNode p, TreeNode q) {
        return check(p,q);
    }
    boolean check(TreeNode p,TreeNode q){
        if(p==null && q==null) return true;
        if(p==null || q==null) return false;
        if(q.val!=p.val) return false;
        return check(p.left,q.left) && check(p.right,q.right);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 