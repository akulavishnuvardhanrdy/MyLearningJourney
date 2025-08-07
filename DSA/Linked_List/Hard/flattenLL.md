# Question

Given a linked list containing n head nodes where every node in the linked list contains two pointers:
(i) next points to the next node in the list.
(ii) bottom pointer to a sub-linked list where the current node is the head.
Each of the sub-linked lists nodes and the head nodes are sorted in ascending order based on their data.
Your task is to flatten the linked list such that all the nodes appear in a single level while maintaining the sorted order.

Note:
1. ↓ represents the bottom pointer and -> represents the next pointer.
2. The flattened list will be printed using the bottom pointer instead of the next pointer.



##### Example:

Input:
5 7 8 30
10 20
19 22 50
28 35 40 45

Output: 5-> 7-> 8-> 10 -> 19-> 20-> 22-> 28-> 30-> 35-> 40-> 45-> 50.

Explanation: 
Bottom pointer of 5 is pointing to 7.
Bottom pointer of 7 is pointing to 8.
Bottom pointer of 8 is pointing to 10 and so on.



### Solve: [https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)
   


# Optimal Solution:  


``` java
    Node flatten(Node root) {
        PriorityQueue<Node> q = new PriorityQueue<>((a,b)->a.data-b.data);
        Node curr = root;
        while(curr!=null){
            q.offer(curr);
            curr = curr.next;
        }
        Node dummy = new Node(-1);
        Node temp = dummy;
        while(!q.isEmpty()){
            curr = q.poll();
            temp.bottom = curr;
            if(curr.bottom!=null) q.offer(curr.bottom);
            temp = temp.bottom;
        }
        // temp.bottom = null;
        return dummy.bottom;
    }
```
### Time Complexity: O(N*logN)+O(N*M*logN)
### Space Complexity: O(N)