# Question

GGiven a doubly linked list of n nodes sorted by values, the task is to remove duplicate nodes present in the linked list.



##### Example:

Input:
n = 6
1<->1<->1<->2<->3<->4

Output:
1<->2<->3<->4

Explanation:
Only the first occurance of node with value 1 is 
retained, rest nodes with value = 1 are deleted.


### Solve: [https://www.geeksforgeeks.org/problems/remove-duplicates-from-a-sorted-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/remove-duplicates-from-a-sorted-doubly-linked-list/1)
   


# Optimal Solution:  


``` java
    Node removeDuplicates(Node head) {
        // Code Here.
        Node dummy = new Node(-1),temp = dummy;
        Node curr = head;
        while(curr!=null){
            if(temp.data!=curr.data){
                temp.next = curr;
                curr.prev = temp;
                temp = temp.next;
            }
            curr = curr.next;
        }
        temp.next = null;
        if(dummy.next!=null)
            dummy.next.prev = null;
        return dummy.next;
    }
```
### Time Complexity: O(N)
### Space Complexity: O(1)