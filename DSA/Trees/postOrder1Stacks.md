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
        TreeNode curr = root;
        while(curr!=null || !st.isEmpty()){
            if(curr!=null){
                st.push(curr);
                curr = curr.left;
            }
            else{
                TreeNode temp = st.peek().right;
                if(temp==null){
                    temp = st.pop();
                    node.add(temp.val);
                    while(!st.isEmpty() && 
                        temp==st.peek().right){
                            temp = st.pop();
                            node.add(temp.val);
                    }
                }
                else
                    curr = temp;
            }
        }
        return node;
    }
```
### Time Complexity: O(2N)  
### Space Complexity: O(N) 