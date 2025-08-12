# Question

Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

Implement the MyQueue class:

void push(int x) Pushes element x to the back of the queue.
int pop() Removes the element from the front of the queue and returns it.
int peek() Returns the element at the front of the queue.
boolean empty() Returns true if the queue is empty, false otherwise.
Notes:

You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid.
Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.



##### Example:

Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]

Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false



### Solve: [https://leetcode.com/problems/implement-queue-using-stacks/](https://leetcode.com/problems/implement-queue-using-stacks/)
   


# Optimal Solution:  


``` java
class MyQueue {
    ArrayDeque<Integer> s1,s2;
    public MyQueue() {
        s1 = new ArrayDeque<>();
        s2 = new ArrayDeque<>();
    }
    
    public void push(int x) {
        int len = s1.size();
        for(int i=0;i<len;++i){
            s2.addLast(s1.pollLast());
        }
        s1.addLast(x);
        len = s2.size();
        for(int i=0;i<len;++i){
            s1.addLast(s2.pollLast());
        }
    }
    
    public int pop() {
        return s1.pollLast();
    }
    
    public int peek() {
        return s1.peekLast();
    }
    
    public boolean empty() {
        return s1.isEmpty();
    }
}
```
### Time Complexity: O(2n) for push O(1) for remaining
### Space Complexity: O(1)