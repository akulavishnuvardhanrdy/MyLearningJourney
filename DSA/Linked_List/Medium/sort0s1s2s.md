# Question

Given the head of a linked list where nodes can contain values 0s, 1s, and 2s only. Your task is to rearrange the list so that all 0s appear at the beginning, followed by all 1s, and all 2s are placed at the end.

##### Example:

Input: head = 1 → 2 → 2 → 1 → 2 → 0 → 2 → 2

Output: 0 → 1 → 1 → 2 → 2 → 2 → 2 → 2

Explanation: All the 0s are segregated to the left end of the linked list, 2s to the right end of the list, and 1s in between.



### Solve: [https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1](https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1)
   


# Optimal Solution:  


``` java
    static Node segregate(Node head) {
        // code here
        Node dummy0 = new Node(0),head0 = dummy0; 
        Node dummy1 = new Node(0), head1 = dummy1;
        Node dummy2 = new Node(0), head2 = dummy2;
        Node curr = head;
        while(curr!=null){
            switch(curr.data){
                case 0:
                    dummy0.next = curr;
                    dummy0 = dummy0.next;
                    break;
                case 1:
                    dummy1.next = curr;
                    dummy1 = dummy1.next;
                    break;
                case 2:
                    dummy2.next = curr;
                    dummy2 = dummy2.next;
            }
            curr = curr.next;
        }
        dummy0.next = head1.next!=null? head1.next : head2.next;
        dummy1.next = head2.next;
        dummy2.next = null;
        return head0.next;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)