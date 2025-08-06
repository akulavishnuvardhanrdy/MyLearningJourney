# Question

Given the head of a linked list, determine whether the list contains a loop. If a loop is present, return the number of nodes in the loop, otherwise return 0.

Note: 'c' is the position of the node which is the next pointer of the last node of the linkedlist. If c is 0, then there is no loop.



##### Example:

Input: head: 1 → 2 → 3 → 4 → 5, c = 2

Output: 4

Explanation: There exists a loop in the linked list and the length of the loop is 4.



### Solve: [https://www.geeksforgeeks.org/problems/find-length-of-loop/1](https://www.geeksforgeeks.org/problems/find-length-of-loop/1)
   


# Optimal Solution:  


``` java
    public int lengthOfLoop(Node head) {
        // code here.
        Node slow = head, fast = head;
        if(head==null || head.next==null) return 0;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast)
                break;
        }
        if(slow == fast){
            fast = fast.next;
            int count = 1;
            while(fast!=slow){
                count++;
                fast = fast.next;
            }
            return count;
        }
        return 0;
    }
```
### Time Complexity: O(2*N)  
### Space Complexity: O(1)