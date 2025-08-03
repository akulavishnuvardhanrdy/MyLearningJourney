# Question

You are given an array nodes. It contains 7 integers, which represents the value of nodes of the binary tree in level order traversal. You are also given a root of the tree which has a value equal to nodes[0].

Your task to construct a binary tree by creating nodes for the remaining 6 nodes.

##### Example:

Input: 
nodes = [1 2 3 4 5 6 7]
Output: 
         1
       /   \
     2       3
   /  \     /  \
   4  5    6   7
Explanation: 
The 7 node binary tree is represented above.

### Solve: [https://www.geeksforgeeks.org/problems/binary-tree-representation/1](https://www.geeksforgeeks.org/problems/binary-tree-representation/1)
   


# Optimal Solution:  
``` java
    public static void createTree(Node root0, ArrayList<Integer> v) {
        Node[] node = new Node[7];
        for(int i=0;i<7;++i){
            node[i] = new Node(v.get(i));
        }
        for(int i=0;i<7;++i){
            int left = 2*i+1;
            int right = 2*i+2;
            if(left<7) node[i].left = node[left];
            if(right<7) node[i].right = node[right];
        }
        root0.val = node[0].val;
        root0.left = node[0].left;
        root0.right = node[0].right;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 