# Question

Given an infix expression in the form of string s. Convert this infix expression to a postfix expression.

Infix expression: The expression of the form a op b. When an operator is in between every pair of operands.
Postfix expression: The expression of the form a b op. When an operator is followed for every pair of operands.
Note: The order of precedence is: ^ greater than * equals to / greater than + equals to -. Ignore the right associativity of ^.



##### Example:

Input: s = "a+b*(c^d-e)^(f+g*h)-i"

Output: abcd^e-fgh*+^*+i-

Explanation: After converting the infix expression into postfix expression, the resultant expression will be abcd^e-fgh*+^*+i-



### Solve: [https://www.geeksforgeeks.org/problems/infix-to-postfix-1587115620/1](https://www.geeksforgeeks.org/problems/infix-to-postfix-1587115620/1)
   


# Optimal Solution:  


``` java
    public static String infixToPostfix(String s) {
        // code here
        ArrayDeque<Character> st = new ArrayDeque<>();
        StringBuilder res = new StringBuilder();
        for(char c : s.toCharArray()){
            if(Character.isLetter(c)){
                res.append(c);
            }
            else if(c=='('){
                st.addLast('(');
            }
            else if(c==')'){
                while(!st.isEmpty() && st.peekLast()!='('){
                    res.append(st.pollLast());
                }
                st.pollLast();
            }
            else{
                while(!st.isEmpty() && precedence(st.peekLast())<=precedence(c) && st.peekLast()!='('){
                    res.append(st.pollLast());
                }
                st.addLast(c);
            }
        }
        while(!st.isEmpty()){
            res.append(st.pollLast());
        }
        return res.toString();
    }
    
    public static int precedence(char c){
        switch(c){
            case '(':
                return 0;
            case '^':
                return 1;
            case '*':
            case '/':
                return 2;
            case '+':
            case '-':
                return 3;
        }
        return -1;
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)