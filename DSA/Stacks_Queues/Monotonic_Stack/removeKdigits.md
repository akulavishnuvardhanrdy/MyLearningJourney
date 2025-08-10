# Question

Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.


##### Example:

Input: num = "1432219", k = 3

Output: "1219"

Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.



### Solve: [https://leetcode.com/problems/remove-k-digits/](https://leetcode.com/problems/remove-k-digits/)
   


# Optimal Solution:  


``` java
    public String removeKdigits(String num, int k) {
        StringBuilder str = new StringBuilder();
        ArrayDeque<Character> st = new ArrayDeque<>();
        if(num.length()==k)
            return "0";
        for(char i: num.toCharArray()){
            while(!st.isEmpty() && k>0 && st.peekLast()>i){
                st.pollLast();
                k--;
            }
            st.addLast(i);
        }
        while(k>0 && !st.isEmpty()){
            st.pollLast();
            k--;
        }
        while(!st.isEmpty() && st.peekFirst()=='0') 
            st.pollFirst();
        while(!st.isEmpty()){
            str.append(st.pollFirst());
        }
        if(str.length()==0)
            return "0";
        return str.toString();
    }
```
### Time Complexity: O(2*n)
### Space Complexity: O(n)