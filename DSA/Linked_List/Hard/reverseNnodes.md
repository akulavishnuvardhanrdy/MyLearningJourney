# Question

Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.


##### Example:

Input: head = [1,2,3,4,5], k = 2

Output: [2,1,4,3,5]



### Solve: [https://leetcode.com/problems/reverse-nodes-in-k-group/](https://leetcode.com/problems/reverse-nodes-in-k-group/)
   


# Optimal Solution:  


``` java
    public ListNode reverseKGroup(ListNode head, int k) {
        if(head==null || k==1) 
            return head;
        ListNode node = head;
        for(int i=0;i<k;++i){
            if(node==null) return head;
            node = node.next;
        }
        ListNode prev = null, curr = head, next = null;
        for(int i=0;i<k;++i){
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        head.next = reverseKGroup(curr,k);
        return prev;
    }
```
### Time Complexity: O(N/K)*O(K)
### Space Complexity: O(N/K)