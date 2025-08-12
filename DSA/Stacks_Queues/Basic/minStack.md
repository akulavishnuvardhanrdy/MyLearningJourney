# Question

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the MinStack class:

MinStack() initializes the stack object.
void push(int val) pushes the element val onto the stack.
void pop() removes the element on the top of the stack.
int top() gets the top element of the stack.
int getMin() retrieves the minimum element in the stack.
You must implement a solution with O(1) time complexity for each function.



##### Example:

Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2




### Solve: [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)
   


# Optimal Solution:  


``` java
class MinStack {
    ArrayDeque<int[]> st;

    public MinStack() {
        st = new ArrayDeque<>();
        st.addLast(new int[]{0,Integer.MAX_VALUE});
    }
    
    public void push(int val) {
        st.addLast(new int[]{val,Math.min(getMin(),val)});
    }
    
    public void pop() {
        st.pollLast();
    }
    
    public int top() {
        return st.peekLast()[0];
    }
    
    public int getMin() {
        return st.peekLast()[1];
    }
}
```
### Time Complexity: O(1)
### Space Complexity: O(1)