# Question

Implement a Queue using Linked List. 
A Query Q is of 2 Types
(i) 1 x   (a query of this type means  pushing 'x' into the queue)
(ii) 2     (a query of this type means to pop an element from the queue and print the poped element)



##### Example:

Input: Q = 5, Queries = [[1, 2], [1, 3], [2], [1, 4], [2]]

Output: 2 3 

Explanation: 
[1,2] queue will be 2
[1,3] queue will be 2,3
[2] poped element will be 2 the queue will be 3
[1, 4] queue will be 3, 4
[2] poped element will be 3 




### Solve: [https://www.geeksforgeeks.org/problems/implement-queue-using-linked-list/1](https://www.geeksforgeeks.org/problems/implement-queue-using-linked-list/1)
   


# Optimal Solution:  


``` java
class MyQueue {
    QueueNode front, rear;

    // Function to push an element into the queue.
    void push(int a) {
        // code here
        QueueNode temp = new QueueNode(a);
        if(rear==null){
            front = temp;
            rear = temp;
        }
        else{
            rear.next = temp;
            rear = rear.next;
        }
    }

    // Function to pop front element from the queue
    int pop() {
        if(front==null)
            return -1;
        int val = front.data;
        front = front.next;
        if(front==null)
            rear = null;
        return val;
        // code here
    }
}
```
### Time Complexity: O(1)
### Space Complexity: O(1)