# Question

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).


##### Example:

Input: root = [3,9,20,null,null,15,7]

Output: [[3],[20,9],[15,7]]


### Solve: [https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
   


# Optimal Solution:  
``` java
    ArrayList<Integer> boundaryTraversal(Node node) {
        ArrayList<Integer> res = new ArrayList<>();
        if(node==null) return res;
        if(!isLeaf(node)) res.add(node.data);
        LeftNode(node.left,res);
        LeafNode(node,res);
        RightNodesReverse(node.right,res);
        return res;
    }
    
    void LeftNode(Node node, ArrayList<Integer> res){
        if(node==null) return ;
        while(!isLeaf(node)){
            res.add(node.data);
            if(node.left==null) node = node.right;
            else node = node.left;
        }
    }
    
    void LeafNode(Node node,ArrayList<Integer> res){
        if(isLeaf(node)){
            res.add(node.data);
            return;
        }
        if(node.left!=null) LeafNode(node.left,res);
        if(node.right!=null) LeafNode(node.right,res);
    }
    
    void RightNodesReverse(Node node,ArrayList<Integer> res){
        if(node==null) return ;
        Stack<Integer> st = new Stack<>();
        while(!isLeaf(node)){
            st.add(node.data);
            if(node.right==null) node = node.left;
            else node = node.right;
        }
        while(!st.isEmpty()){
            res.add(st.pop());
        }
    }
    
    boolean isLeaf(Node node){
        if(node.left==null && node.right==null)
            return true;
        return false;
    }
```
### Time Complexity: O(N)+O(h)+O(h)  
### Space Complexity: O(1) 