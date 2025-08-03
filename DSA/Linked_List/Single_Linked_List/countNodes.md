# Question

Given head of a singly linked list. The task is to find the length of the linked list, where length is defined as the number of nodes in the linked list.


##### Example:

Input: head : 1->2->3->4->5

Output: 5

Explanation: Length of the linked list is 5, as there 
are 5 nodes present in it.



### Solve: [https://www.geeksforgeeks.org/problems/count-nodes-of-linked-list/1](https://www.geeksforgeeks.org/problems/count-nodes-of-linked-list/1)
   


# Optimal Solution:  
``` java
    public int getCount(Node head) {
        // code here
        int count=0;
        while(head!=null){
            count++;
            head = head.next;
        }
        return count;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)