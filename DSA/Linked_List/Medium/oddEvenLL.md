# Question

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.



##### Example:

Input: head = [1,2,3,4,5]

Output: [1,3,5,2,4]



### Solve: [https://leetcode.com/problems/odd-even-linked-list/](https://leetcode.com/problems/odd-even-linked-list/)
   


# Optimal Solution:  


``` java
    public ListNode oddEvenList(ListNode head) {
        if(head==null || head.next==null) 
            return head;
        ListNode odd = head, even = head.next, evenHead = head.next;
        while(even!=null && even.next!=null){
            odd.next = even.next;
            even.next = even.next.next;
            odd = odd.next;
            even = even.next;
        }
        odd.next = evenHead;
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)