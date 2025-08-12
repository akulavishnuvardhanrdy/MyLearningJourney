# Question

Given a valid arithmetic expression in infix notation, return its equivalent prefix (Polish) notation.



The expression can contain:

lowercase letters a–z as operands,
the four binary operators + - * /,
and round parentheses ( ) that enforce evaluation order.
No whitespace appears in the input.


The input is guaranteed to be syntactically correct (parentheses are balanced, every operator has two operands, etc.).



##### Example:

Input: "(a+b)*c"

Output: "*+abc"

Explanation:

 Infix  : (a + b) * c
 Prefix : * + a b c



### Solve: [https://takeuforward.org/plus/dsa/problems/infix-to-prefix-conversion](https://takeuforward.org/plus/dsa/problems/infix-to-prefix-conversion)
   


# Optimal Solution:  


``` java
    public String infixToPrefix(String s) {
    // Your code goes here
    ArrayDeque<Character> st = new ArrayDeque<>();
    StringBuilder res = new StringBuilder();
    for (int i = s.length() - 1; i >= 0; --i) {
      char c = s.charAt(i);
      if (Character.isLetter(c)) {
        res.append(c);
      } else if (c == ')') {
        st.addLast(c);
      } else if (c == '(') {
        while (st.peekLast() != ')') res.append(st.pollLast());
        st.pollLast();
      } else {
        while (!st.isEmpty()
            && precedence(st.peekLast()) <= precedence(c)
            && st.peekLast() != ')') {
          res.append(st.pollLast());
        }
        st.addLast(c);
      }
    }
    while(!st.isEmpty()){
        res.append(st.pollLast());
    }
    return res.reverse().toString();
  }

  public int precedence(char c) {
    switch (c) {
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