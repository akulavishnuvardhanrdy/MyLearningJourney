# Question

You are given a string S of size N that represents the prefix form of a valid mathematical expression. The string S contains only lowercase and uppercase alphabets as operands and the operators are +, -, *, /, %, and ^.Convert it to its infix form.



##### Example:

Input: 
*-A/BC-/AKL

Output: 
((A-(B/C))*((A/K)-L))

Explanation: 
The above output is its valid infix form.



### Solve: [https://www.geeksforgeeks.org/problems/prefix-to-infix-conversion/1](https://www.geeksforgeeks.org/problems/prefix-to-infix-conversion/1)
   


# Optimal Solution:  


``` java
    static String preToInfix(String str) {
        // code here
        ArrayDeque<String> st = new ArrayDeque<>();
        for(int i=str.length()-1;i>=0;--i){
            if(Character.isLetter(str.charAt(i)))
                st.addLast(str.charAt(i)+"");
            else{
                String temp = "("+st.pollLast()+str.charAt(i)+st.pollLast()+")";
                st.addLast(temp);
            }
        }
        return st.pollLast();
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)