# Question

You are given a string that represents the postfix form of a valid mathematical expression. Convert it to its prefix form.You are given a string that represents the postfix form of a valid mathematical expression. Convert it to its prefix form.



##### Example:

Input: 
ABC/-AK/L-*

Output: 
*-A/BC-/AKL

Explanation: 
The above output is its valid prefix form.



### Solve: [https://www.geeksforgeeks.org/problems/postfix-to-prefix-conversion/1](https://www.geeksforgeeks.org/problems/postfix-to-prefix-conversion/1)
   


# Optimal Solution:  


``` java
    static String postToPre(String post_exp) {
        // code here
        ArrayDeque<String> st = new ArrayDeque<>();
        for(char c: post_exp.toCharArray()){
            if(Character.isLetter(c)){
                st.addLast(c+"");
            }
            else{
                String right = st.pollLast();
                String left = st.pollLast();
                String temp = c + left + right;
                st.addLast(temp);
            }
        }
        return st.pollLast();
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)