# Question

You are given a linked list where each element in the list is a node and have an integer data. You need to add 1 to the number formed by concatinating all the list node numbers together and return the head of the modified linked list. 

Note: The head represents the first element of the given array.



##### Example:

Input: LinkedList: 4->5->6

Output: 457

Explanation: 4->5->6 represents 456 and when 1 is added it becomes 457


### Solve: [https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1](https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1)
   


# Optimal Solution:  


``` java
    public Node addOne(Node head) {
        // code here.
        int carry = plusOne(head); 
        if(carry>0){
            Node temp = new Node(carry);
            temp.next = head;
            return temp;
        }
        return head;
    }
    int plusOne(Node head){
        if(head==null)
            return 1;
        int carry = plusOne(head.next);
        int sum = head.data + carry;
        head.data = sum%10;
        return sum/10;
    }
```
### Time Complexity: O(N)
### Space Complexity: O(1)