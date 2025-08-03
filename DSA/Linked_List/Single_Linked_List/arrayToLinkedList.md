# Question

Given an array of integer arr. Your task is to construct the linked list from arr & return the head of the linked list.

##### Example:

Input: arr = [1, 2, 3, 4, 5]

Output: LinkedList: 1->2->3->4->5

Explanation: Linked list for the given array will be



### Solve: [https://www.geeksforgeeks.org/problems/introduction-to-linked-list/1](https://www.geeksforgeeks.org/problems/introduction-to-linked-list/1)
   


# Optimal Solution:  
``` java
    static Node constructLL(int arr[]) {
        List<Node> ll = new LinkedList<>();
        Node head = new Node(arr[0]);
        Node curr = head;
        for(int i=1;i<arr.length;++i){
            Node temp = new Node(arr[i]);
            curr.next=temp;
            curr = temp;
        }
        return head;
    }
```
### Time Complexity: O(N)  
### Space Complexity: O(N)