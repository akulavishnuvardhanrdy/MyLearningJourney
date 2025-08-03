# Question

Given a linked list of n nodes and a key, the task is to check if the key is present in the linked list or not.


##### Example:

Input: n = 4, key = 3
1->2->3->4

Output: true

Explanation: 3 is present in Linked List, so the function returns true.



### Solve: [https://www.geeksforgeeks.org/problems/search-in-linked-list-1664434326/1](https://www.geeksforgeeks.org/problems/search-in-linked-list-1664434326/1)
   


# Optimal Solution:  
``` java
    static boolean searchKey(int n, Node head, int key) {
        // Code here
        while(head!=null){
            if(head.data==key)
                return true;
            head = head.next;
        }
        return false;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(1)