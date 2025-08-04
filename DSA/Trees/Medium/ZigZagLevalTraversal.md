# Question

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).


##### Example:

Input: root = [3,9,20,null,null,15,7]

Output: [[3],[20,9],[15,7]]


### Solve: [https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
   


# Optimal Solution:  
``` java
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        Queue<TreeNode> q = new LinkedList<>();
        if(root==null) return res;
        boolean flag = true;
        q.add(root);
        while(!q.isEmpty()){
            int len = q.size();
            List<Integer> ls = new ArrayList<>();
            while(len!=0){
                TreeNode temp = q.poll();
                if(flag) ls.addLast(temp.val);
                else ls.addFirst(temp.val);
                if(temp.left!=null) q.add(temp.left);
                if(temp.right!=null) q.add(temp.right);
                len--;
            }
            res.add(ls);
            flag = !flag;
        }
        return res;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N) 