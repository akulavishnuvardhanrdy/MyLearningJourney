# Question

Given the head of a singly linked list, reverse the list, and return the reversed list.




##### Example:

Input: head = [1,2,3,4,5]

Output: [5,4,3,2,1]



### Solve: [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
   


# Optimal Solution:  


``` java
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
### Time Complexity: O(N)  
### Space Complexity: O(1)