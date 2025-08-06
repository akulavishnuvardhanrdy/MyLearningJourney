# Question

You are given the head_ref of a doubly Linked List and a Key. Your task is to delete all occurrences of the given key if it is present and return the new DLL.



##### Example:

Input: 
2<->2<->10<->8<->4<->2<->5<->2
2

Output: 
10<->8<->4<->5

Explanation: 
All Occurences of 2 have been deleted.


### Solve: [https://www.geeksforgeeks.org/problems/delete-all-occurrences-of-a-given-key-in-a-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/delete-all-occurrences-of-a-given-key-in-a-doubly-linked-list/1)
   


# Optimal Solution:  


``` java
    static Node deleteAllOccurOfX(Node head, int x) {
        Node curr = head;
        while(curr!=null){
            if(curr.data==x){
                Node prev = curr.prev;
                Node next = curr.next;
                if(prev!=null)
                    prev.next = next;
                else
                    head = next;
                if(next!=null)
                    next.prev = prev;
            }
            curr = curr.next;
        }
        return head;
    }
```
### Time Complexity: O(N)
### Space Complexity: O(1)