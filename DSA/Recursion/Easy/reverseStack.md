# Question  

You are given a stack St. Implement an algorithm to reverse the stack using recursion.



##### Examples :

Input: St = [3, 2, 1, 7, 6]

Output: [6, 7, 1, 2, 3]

Explanation: Input stack after reversing will look like the stack in the output.



### Solve: [https://www.geeksforgeeks.org/problems/reverse-a-stack/1](https://www.geeksforgeeks.org/problems/reverse-a-stack/1)

*** 

# Optimal Solution 

``` java
    static void reverse(Stack<Integer> st) {
        // code here
        if(st.isEmpty())
            return ;
        int temp = st.pop();
        reverse(st);
        insert(temp,st);
    }
    static void insert(int temp,Stack<Integer> st){
        if(st.isEmpty()){
            st.push(temp);
            return ;
        }
        int top = st.pop();
        insert(temp,st);
        st.push(top);
    }
```

### Time Complexity: O(N^2)  
### Space Complexity: O(N) 