# Question

Given the root of a binary tree, return the inorder traversal of its nodes' values.


##### Example:

Input: root = [1,null,2,3]

Output: [1,3,2]



### Solve: [https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)
   


# Optimal Solution:  
``` java
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> node = new ArrayList<>();
        inorder(root,node);
        return node;
    }
    void inorder(TreeNode root,List<Integer> node){
        if(root==null)
            return ;
        inorder(root.left,node);
        node.add(root.val);
        inorder(root.right,node);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 