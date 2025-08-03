# Question

Given the root of a binary tree, return the postorder traversal of its nodes' values.


##### Example:

Input: root = [1,null,2,3]

Output: [3,2,1]



### Solve: [https://leetcode.com/problems/binary-tree-postorder-traversal/](https://leetcode.com/problems/binary-tree-postorder-traversal/)
   


# Optimal Solution:  
``` java
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> node = new ArrayList<>();
        postorder(root,node);
        return node;
    }
    void postorder(TreeNode root,List<Integer> node){
        if(root==null)
            return ;
        postorder(root.left,node);
        postorder(root.right,node);
        node.add(root.val);
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 