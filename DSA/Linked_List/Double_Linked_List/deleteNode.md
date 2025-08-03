# Question

Given a Doubly Linked list and a position. The task is to delete a node from a given position (position starts from 1) in a doubly linked list and return the head of the doubly Linked list.



##### Example:

Input: LinkedList = 1 <--> 3 <--> 4, x = 3

Output: 1 <--> 3

Explanation: After deleting the node at position 3 (position starts from 1),the linked list will be now as 1 <--> 3.



### Solve: [https://www.geeksforgeeks.org/problems/delete-node-in-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/delete-node-in-doubly-linked-list/1)
   


# Optimal Solution:  
``` java
    public Node deleteNode(Node head, int x) {
        int idx = 1;
        Node curr = head;
        Node prev = null;
        if(head.next==null) return null; 
        while(curr!=null){
            if(idx==x){
                if(prev==null){
                    head.next.prev = null;
                    return head.next;
                }
                prev.next = curr.next;
                if(curr.next!=null)
                    curr.next.prev = prev;
                break;
            }
            prev = curr;
            curr=curr.next;
            idx++;
        }
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)