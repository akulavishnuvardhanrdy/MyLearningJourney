# Question

Given a string s containing only three types of characters: '(', ')' and '*', return true if s is valid.

The following rules define a valid string:

Any left parenthesis '(' must have a corresponding right parenthesis ')'.
Any right parenthesis ')' must have a corresponding left parenthesis '('.
Left parenthesis '(' must go before the corresponding right parenthesis ')'.
'*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string "".



##### Example:

Input: s = "()"

Output: true



### Solve: [https://leetcode.com/problems/valid-parenthesis-string/](https://leetcode.com/problems/valid-parenthesis-string/)

***

# Optimal Solution
        

``` java
    public boolean checkValidString(String s) {
        int low = 0, high = 0;
        for(char ch:s.toCharArray()){
            if(ch=='('){
                low++;
                high++;
            }
            else if(ch==')'){
                low--;
                high--;
            }
            else{
                low--;
                high++;
            }
            if(high<0) return false;
            if(low<0) low = 0;
        }
        return low==0;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)