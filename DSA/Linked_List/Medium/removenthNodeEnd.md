# Question

Given the head of a linked list, remove the nth node from the end of the list and return its head.



##### Example:

Input: head = [1,2,3,4,5], n = 2

Output: [1,2,3,5]



### Solve: [https://leetcode.com/problems/remove-nth-node-from-end-of-list/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
   


# Optimal Solution:  


``` java
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head.next == null) return null;
        ListNode fast = head, slow = head;
        for (int i = 0; i < n; i++) {
            fast = fast.next;
        }
        if(fast==null)
            return head.next;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next;
        }
        slow.next = slow.next.next;
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)