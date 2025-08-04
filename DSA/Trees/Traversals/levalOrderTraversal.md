# Question

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level)


##### Example:

Input: root = [3,9,20,null,null,15,7]

Output: [[3],[9,20],[15,7]]



### Solve: [https://leetcode.com/problems/binary-tree-level-order-traversal/description/](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)
   


# Optimal Solution:  
``` java
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> node = new ArrayList<>();
        Queue<TreeNode> q = new LinkedList<>();
        if(root==null) return node;
        q.add(root);
        while(!q.isEmpty()){
            List<Integer> subnode = new ArrayList<>();
            int len = q.size();
            while(len!=0){
                TreeNode temp = q.poll();
                if(temp.left!=null) q.add(temp.left);
                if(temp.right!=null) q.add(temp.right);
                subnode.add(temp.val);
                len--;
            }
            node.add(subnode);
        }
        return node;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 