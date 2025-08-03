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
        Stack<TreeNode> st = new Stack<>();
        TreeNode curr = root;
        while(curr!=null || !st.isEmpty()){
            while(curr!=null){
                st.add(curr);
                curr = curr.left;
            }
            curr = st.pop();
            node.add(curr.val);
            curr = curr.right;
        }
        return node;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 