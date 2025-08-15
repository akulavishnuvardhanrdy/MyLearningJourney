# Question

Given a valid parentheses string s, return the nesting depth of s. The nesting depth is the maximum number of nested parentheses.



##### Example:

Input: s = "(1+(2*3)+((8)/4))+1"

Output: 3

Explanation:

Digit 8 is inside of 3 nested parentheses in the string.


### Solve: [https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)

***

# Optimal Solution
        

``` java
    public int maxDepth(String s) {
        int depth = 0;
        int maxDepth = 0;
        for(int i=0;i<s.length();++i){
            char c = s.charAt(i);
            if(c=='('){
                depth++;
            }
            if(c==')'){
                depth--;
            }
            maxDepth = Math.max(maxDepth,depth);
        }
        return maxDepth;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)