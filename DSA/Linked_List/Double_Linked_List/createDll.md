# Question

Geek is learning data structures and is familiar with linked lists, but he's curious about how to access the previous element in a linked list in the same way that we access the next element. His teacher explains doubly linked lists to him.

Given an integer array arr of size n. Construct the doubly linked list from arr and return the head of it.


##### Example:

Input:
n = 5
arr = [1,2,3,4,5]

Output:
1 2 3 4 5

Explanation: Linked list for the given array will be 1<->2<->3<->4<->5.



### Solve: [https://www.geeksforgeeks.org/problems/introduction-to-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/introduction-to-doubly-linked-list/1)
   


# Optimal Solution:  
``` java
    Node constructDLL(int arr[]) {
        // Code here
        Node head = new Node(arr[0]);
        head.prev = null;
        Node curr = head;
        for(int i=1;i<arr.length;++i){
            Node temp = new Node(arr[i]);
            temp.prev = curr;
            curr.next = temp;
            curr = curr.next;
        }
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N)