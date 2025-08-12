# Question

You are given a string that represents the prefix form of a valid mathematical expression. Convert it to its postfix form.



##### Example:

Input: 
*-A/BC-/AKL

Output: 
ABC/-AK/L-*

Explanation: 
The above output is its valid postfix form.



### Solve: [https://www.geeksforgeeks.org/problems/prefix-to-postfix-conversion/1](https://www.geeksforgeeks.org/problems/prefix-to-postfix-conversion/1)
   


# Optimal Solution:  


``` java
    static String preToPost(String str) {
        // code here
        ArrayDeque<String> st = new ArrayDeque<>();
        for(int i=str.length()-1;i>=0;--i){
            if(Character.isLetter(str.charAt(i))){
                st.addLast(str.charAt(i)+"");
            }
            else{
                String temp = st.pollLast()+st.pollLast()+str.charAt(i);
                st.addLast(temp);
            }
        }
        return st.pollLast();
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)