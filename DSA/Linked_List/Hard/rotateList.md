# Question

Given the head of a linked list, rotate the list to the right by k places.


##### Example:

Input: head = [1,2,3,4,5], k = 2

Output: [4,5,1,2,3]



### Solve: [https://leetcode.com/problems/rotate-list/](https://leetcode.com/problems/rotate-list/)
   


# Optimal Solution:  


``` java
    public ListNode rotateRight(ListNode head, int k) {
        int len = 0;
        ListNode curr = head;
        if(head==null) return head;
        while(curr!=null){
            curr = curr.next;
            len++;
        }
        k = k%len;
        ListNode fast = head,slow = head;
        for(int i=0;i<k;++i){
            fast = fast.next;
        }
        while(fast.next!=null){
            fast = fast.next;
            slow = slow.next;
        }
        fast.next = head;
        head = slow.next;
        slow.next = null;
        return head;
    }
```
### Time Complexity: O(N)
### Space Complexity: O(1)