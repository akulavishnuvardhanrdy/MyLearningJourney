# Question

Given the head of a linked list, return the list after sorting it in ascending order.


##### Example:

Input: head = [4,2,1,3]

Output: [1,2,3,4]



### Solve: [https://leetcode.com/problems/sort-list/](https://leetcode.com/problems/sort-list/)
   


# Optimal Solution:  


``` java
    public ListNode sortList(ListNode head) {
        if(head==null || head.next==null)
            return head;
        ListNode mid = findMiddle(head);
        ListNode right = mid.next;
        mid.next = null;
        ListNode lsorted = sortList(head);
        ListNode rsorted = sortList(right);
        return merge(lsorted,rsorted);
    }

    ListNode findMiddle(ListNode head){
        ListNode fast = head, slow = head;
        while(fast.next!=null && fast.next.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    ListNode merge(ListNode left, ListNode right){
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;
        while(left!=null && right!=null){
            if(left.val<=right.val){
                tail.next = left;
                left = left.next;
            }
            else{
                tail.next = right;
                right = right.next;
            }
            tail = tail.next;
            
            tail.next = (left!=null)? left:right;
        }
        return dummy.next;
    }
```
### Time Complexity: O(N*logN)+O(N/2*logN)  
### Space Complexity: O(1)