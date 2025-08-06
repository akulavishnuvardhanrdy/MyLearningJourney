# Question

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.



##### Example:

Input: head = [1,2,2,1]

Output: true



### Solve: [https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)
   


# Optimal Solution:  


``` java
    public boolean isPalindrome(ListNode head) {
        if(head.next==null) return true;
        ListNode slow = head, fast = head;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        if(fast!=null && fast.next==null)
            slow = slow.next;
        ListNode sec = reverseList(slow);
        ListNode first = head;
        while(sec!=null){
            if(sec.val!=first.val)
                return false;
            sec = sec.next;
            first = first.next;
        }
        return true;
    }


    public ListNode reverseList(ListNode head) {
        if(head==null || head.next==null) return head;
        ListNode temp=head.next,prev=head,next=head.next;
        prev.next = null;
        while(temp!=null){
            next = temp.next;
            temp.next = prev;
            prev = temp;
            temp = next;
        }
        return prev;
    }
```
### Time Complexity: O(N/2)*O(N/2)*O(N/2)  
### Space Complexity: O(1)