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
        Stack<TreeNode> st = new Stack<>();
        if(root == null) 
            return node;
        st.add(root);
        while(!st.isEmpty()){
            TreeNode curr = st.pop();
            node.add(curr.val);
            if(curr.right!=null) st.add(curr.right);
            if(curr.left!=null) st.add(curr.left);
        }
        return node;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 