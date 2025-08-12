# Question

Write a program to implement a stack using an array oper[]. You need  to complete the push(int x) and pop() methods inside a class MyStack to simulate the standard stack operations:
push(x): Pushes the integer x onto the stack.
pop(): Removes and returns the topmost element of the stack. If the stack is empty, return -1.
You will be given a list of space-separated queries consisting of two types:
Type 1 : 1 x — Push x into the stack.
Type 2 : 2  — Pop the top element from the stack and print it. If the stack is empty, print -1.
Note: It is guaranteed that for Type 1, there will always be a value x.



##### Example:

Input: oper[] = [1, 2, 1, 3, 2, 1, 4, 2] 
Output: [3, 4]
Explanation: 
push(2)   the stack will be {2}
push(3)   the stack will be {2 3}
pop()     poped element will be 3, the stack will be {2}
push(4)   the stack will be {2 4}
pop()     poped element will be 4




### Solve: [https://www.geeksforgeeks.org/problems/implement-stack-using-array/1](https://www.geeksforgeeks.org/problems/implement-stack-using-array/1)
   


# Optimal Solution:  


``` java
class MyStack {
    int arr[];
    int top;
    
    public MyStack(){
        top = 0;
        arr = new int[1000];
    }
    
    public void push(int x) {
        // code here
        if(top==arr.length){
            return ;
        }
        arr[top++] = x;
    }

    public int pop() {
        
        if(top==0){
            return -1;
        }
        return arr[--top];
    }
}
```
### Time Complexity: O(1)
### Space Complexity: O(1)