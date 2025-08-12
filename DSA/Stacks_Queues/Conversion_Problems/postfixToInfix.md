# Question

You are given a string that represents the postfix form of a valid mathematical expression. Convert it to its infix form.



##### Example:

Input:
ab*c+ 

Output: 
((a*b)+c)

Explanation: 
The above output is its valid infix form.



### Solve: [https://www.geeksforgeeks.org/problems/postfix-to-infix-conversion/1](https://www.geeksforgeeks.org/problems/postfix-to-infix-conversion/1)
   


# Optimal Solution:  


``` java
    static String postToInfix(String exp) {
        // code here
        ArrayDeque<String> st = new ArrayDeque<>();
        for(char c: exp.toCharArray()){
            if(Character.isLetter(c)){
                st.addLast(c+"");
            }
            else{
                String right = st.pollLast();
                String left = st.pollLast();
                String temp = "("+left+c+right+")";
                st.addLast(temp);
            }
        }
        return st.pollLast();
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)