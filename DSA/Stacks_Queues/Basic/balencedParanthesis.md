# Question

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.



##### Example:

Input: s = "()"

Output: true




### Solve: [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
   


# Optimal Solution:  


``` java
    public boolean isValid(String s) {
        ArrayDeque<Character> st = new ArrayDeque<>();
        for(char c:s.toCharArray()){
            if(c=='(' || c=='{' || c=='[')
                st.addLast(c);
            else if(st.isEmpty() || (c==')' && st.peekLast()!='('))
                return false;
            else if(st.isEmpty() || (c=='}' && st.peekLast()!='{'))
                return false;
            else if(st.isEmpty() || (c==']' && st.peekLast()!='['))
                return false;
            else
                st.pollLast();
        }
        if(!st.isEmpty())
            return false;
        return true;
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)