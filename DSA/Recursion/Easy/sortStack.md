# Question  

Given a stack of integers st[], Sort the stack in ascending order (smallest element at the bottom and largest at the top).



##### Examples :

Input: st[] = [1, 2, 3]

Output: [1, 2, 3]

Explanation: The stack is already sorted in ascending order.



### Solve: [https://www.geeksforgeeks.org/problems/sort-a-stack/1](https://www.geeksforgeeks.org/problems/sort-a-stack/1)

*** 

# Optimal Solution 

``` java
    public Stack<Integer> sort(Stack<Integer> st) {
        // add code here.
        if(!st.isEmpty()){
            int top = st.pop();
            sort(st);
            insertSort(st,top);
        }
        return st;
    }
    
    void insertSort(Stack<Integer> st,int top){
        if(st.isEmpty() || top>st.peek()){
            st.push(top);
            return;
        }
        int temp = st.pop();
        insertSort(st,top);
        st.push(temp);
    }
```

### Time Complexity: O(N^2)  
### Space Complexity: O(N) 