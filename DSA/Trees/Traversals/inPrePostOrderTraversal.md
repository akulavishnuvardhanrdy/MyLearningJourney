# Question

You have been given a Binary Tree of 'N'

nodes, where the nodes have integer values.



Your task is to return the ln-Order, Pre-Order, and Post-Order traversals of the given binary tree.


##### Example:

For the given binary tree:

The Inorder traversal will be [5, 3, 2, 1, 7, 4, 6].
The Preorder traversal will be [1, 3, 5, 2, 4, 7, 6].
The Postorder traversal will be [5, 2, 3, 7, 6, 4, 1].



### Solve: [https://www.naukri.com/code360/problems/tree-traversal_981269](https://www.naukri.com/code360/problems/tree-traversal_981269)
   


# Optimal Solution:  
``` java
    public static List<List<Integer>> getTreeTraversal(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> in = new ArrayList<>();
        List<Integer> pre = new ArrayList<>();
        List<Integer> post = new ArrayList<>();
        Stack<TreeNode> st = new Stack<>();
        TreeNode curr = root;
        while(curr!=null || !st.isEmpty()){
            while(curr!=null){
                st.push(curr);
                pre.add(curr.data);
                curr = curr.left;
            }
            TreeNode temp = st.peek().right;
            if(temp==null){
                temp = st.pop();
                in.add(temp.data);
                post.add(temp.data);
                while(!st.isEmpty() && 
                    temp==st.peek().right){
                        temp = st.pop();
                        post.add(temp.data);
                }
            }
            else{
                in.add(st.peek().data);
                curr = temp;
            }
        }
        res.add(in);
        res.add(pre);
        res.add(post);
        return res;
    }
```
### Time Complexity: O(3N)  
### Space Complexity: O(3N) +O(N)