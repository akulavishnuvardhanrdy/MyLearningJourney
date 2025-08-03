# Question

Given the head of a doubly-linked list, a position p, and an integer x. The task is to add a new node with value x at the position just after pth node in the doubly linked list and return the head of the updated list.

Note: The position is 0-based indexed.


##### Example:

Input:p = 2, x = 6

Output: 2 4 5 6

Explanation: Insert a node of value 6 after the 2nd node.



### Solve: [https://www.geeksforgeeks.org/problems/insert-a-node-in-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/insert-a-node-in-doubly-linked-list/1)
   


# Optimal Solution:  
``` java
    Node addNode(Node head, int p, int x) {
        // code here
        int idx =0;
        Node curr = head;
        Node temp = new Node(x);
        if(head==null) return temp;
        while(curr!=null){
            if(idx==p){
                temp.next = curr.next;
                curr.next = temp;
                temp.prev = curr;
                break;
            }
            curr = curr.next;
            idx++;
        }
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)