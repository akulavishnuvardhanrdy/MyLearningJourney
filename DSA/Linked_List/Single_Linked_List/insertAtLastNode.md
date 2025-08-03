# Question

Given the head of a Singly Linked List and a value x, insert that value x at the end of the LinkedList and return the modified Linked List.


##### Example:

Input: LinkedList: 1->2->3->4->5 , x = 6

Output: 1->2->3->4->5->6



### Solve: [https://www.geeksforgeeks.org/problems/linked-list-insertion-1587115620/1](https://www.geeksforgeeks.org/problems/linked-list-insertion-1587115620/1)
   


# Optimal Solution:  
``` java
    public Node insertAtEnd(Node head, int x) {
        Node last = new Node(x);
        if(head==null) return last;
        Node temp = head;
        while(temp.next!=null){
            temp = temp.next;
        }
        temp.next = last;
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)