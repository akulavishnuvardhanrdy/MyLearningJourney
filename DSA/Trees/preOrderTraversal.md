# Question

Given the root of a binary tree, return the preorder traversal of its nodes' values.

##### Example:

Input: root = [1,null,2,3]

Output: [1,2,3]



### Solve: [https://leetcode.com/problems/binary-tree-preorder-traversal/description/](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)
   


# Optimal Solution:  
``` java
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> node = new ArrayList<>();
        preorder(root,node);
        return node;
    }
    void preorder(TreeNode root,List<Integer> node){
        if(root==null)
            return ;
        node.add(root.val);
        preorder(root.left,node);
        preorder(root.right,node);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 