# Question

Given a doubly linked list. Your task is to reverse the doubly linked list and return its head.



##### Example:

Input: LinkedList: 3 <-> 4 <-> 5

Output: 5 <-> 4 <-> 3



### Solve: [https://www.geeksforgeeks.org/problems/reverse-a-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/reverse-a-doubly-linked-list/1)
   


# Optimal Solution:  
``` java
    public DLLNode reverseDLL(DLLNode head) {
        DLLNode pnt1 = head, temp, curr = head;
        if(pnt1==null || pnt1.next==null)
            return pnt1;
        pnt1.prev = pnt1.next;
        pnt1.next = null;
        pnt1 = pnt1.prev;
        while(pnt1!=null){
            temp = pnt1.prev;
            pnt1.prev = pnt1.next;
            pnt1.next = temp;
            curr = pnt1;
            pnt1 = pnt1.prev;
        }
        return curr;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)