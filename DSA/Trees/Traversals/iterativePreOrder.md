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
        TreeNode curr = root;
        while(curr!=null || !st.isEmpty()){
            while(curr!=null){
                st.add(curr);
                node.add(curr.val);
                curr = curr.left;
            }
            curr = st.pop();
            curr = curr.right;
        }
        return node;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 