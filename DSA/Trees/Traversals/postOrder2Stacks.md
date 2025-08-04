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
        Stack<TreeNode> st = new Stack<>();
        Stack<Integer> res = new Stack<>();
        if(root==null) 
            return node;
        st.add(root);
        while(!st.isEmpty()){
            TreeNode curr = st.pop();
            res.add(curr.val);
            if(curr.left!=null) st.add(curr.left);
            if(curr.right!=null) st.add(curr.right);
        }
        while(!res.isEmpty()){
            node.add(res.pop());
        }
        return node;
    }
```
### Time Complexity: O(2N)  
### Space Complexity: O(2N) 