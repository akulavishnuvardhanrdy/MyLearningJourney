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
        // Write your code here.
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> in = new ArrayList<>();
        List<Integer> pre = new ArrayList<>();
        List<Integer> post = new ArrayList<>();
        Stack<Pair> st = new Stack<>();
        st.add(new Pair(root,1));
        while(!st.isEmpty()){
            Pair curr = st.peek();
            if(curr.pos==1){
                pre.add(curr.node.data);
                curr.pos++;
                if(curr.node.left!=null) st.add(new Pair(curr.node.left,1));
            }
            else if(curr.pos==2){
                in.add(curr.node.data);
                curr.pos++;
                if(curr.node.right!=null) st.add(new Pair(curr.node.right,1));
            }
            else{
                post.add(curr.node.data);
                st.pop();
            }
        }
        res.add(in);
        res.add(pre);
        res.add(post);
        return res;
    }

    static class Pair{
        TreeNode node;
        int pos;
        Pair(TreeNode node,int pos){
            this.node = node;
            this.pos = pos;
        }
    }
```
### Time Complexity: O(3N)  
### Space Complexity: O(3N) +O(N)