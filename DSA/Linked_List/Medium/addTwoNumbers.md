# Question

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.


##### Example:

Input: l1 = [2,4,3], l2 = [5,6,4]

Output: [7,0,8]

Explanation: 342 + 465 = 807.



### Solve: [https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/)
   


# Optimal Solution:  


``` java
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode dummy = new ListNode(-1),tail = dummy;
        while(l1!=null && l2!=null){
            int val = l1.val + l2.val+carry;
            ListNode temp = new ListNode(val%10);
            carry = val/10;
            tail.next = temp;
            tail = tail.next;
            l1 = l1.next;
            l2 = l2.next;
        }
        while(l1!=null){
            int val = l1.val+carry;
            ListNode temp = new ListNode(val%10);
            carry = val/10;
            tail.next = temp;
            tail = tail.next;
            l1 = l1.next;
        }
        while(l2!=null){
            int val = l2.val+carry;
            ListNode temp = new ListNode(val%10);
            carry = val/10;
            tail.next = temp;
            tail = tail.next;
            l2 = l2.next;
        }
        if(carry>0){
            ListNode temp = new ListNode(carry);
            tail.next = temp;
        }
        return dummy.next;
    }
```
### Time Complexity: O(max(N1,N2))  
### Space Complexity: O(1)