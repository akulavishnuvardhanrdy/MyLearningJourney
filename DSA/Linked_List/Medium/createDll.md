# Question

Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.


##### Example:

Input: head = [1,2,3,4,5]

Output: [3,4,5]

Explanation: The middle node of the list is node 3.



### Solve: [https://leetcode.com/problems/middle-of-the-linked-list/](https://leetcode.com/problems/middle-of-the-linked-list/)
   


# Optimal Solution:  

### Tortoise and Hare Algorithm

``` java
    public ListNode middleNode(ListNode head) {
        ListNode fast = head, slow = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
```
### Time Complexity: O(N/2)  
### Space Complexity: O(1)