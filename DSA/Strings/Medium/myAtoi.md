# Question

Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer.

The algorithm for myAtoi(string s) is as follows:

Whitespace: Ignore any leading whitespace (" ").
Signedness: Determine the sign by checking if the next character is '-' or '+', assuming positivity if neither present.
Conversion: Read the integer by skipping leading zeros until a non-digit character is encountered or the end of the string is reached. If no digits were read, then the result is 0.
Rounding: If the integer is out of the 32-bit signed integer range [-231, 231 - 1], then round the integer to remain in the range. Specifically, integers less than -231 should be rounded to -231, and integers greater than 231 - 1 should be rounded to 231 - 1.
Return the integer as the final result.



##### Example:

Input: s = "42"

Output: 42

Explanation:

The underlined characters are what is read in and the caret is the current reader position.
Step 1: "42" (no characters read because there is no leading whitespace)
         ^
Step 2: "42" (no characters read because there is neither a '-' nor '+')
         ^
Step 3: "42" ("42" is read in)
           ^



### Solve: [https://leetcode.com/problems/string-to-integer-atoi/](https://leetcode.com/problems/string-to-integer-atoi/)

***

# Optimal Solution
        

``` java
    public int myAtoi(String s) {
        s=s.trim();
        if(s.length()==0)
            return 0;
        boolean neg = false;
        long res = 0;
        int i=0;
        if(!Character.isDigit(s.charAt(0))){
            if(s.charAt(0)=='-')
                neg = true;
            else if(s.charAt(0)!='+')
                return 0;
            i++;
        }
        for(;i<s.length();++i){
            char c = s.charAt(i);
            if(!Character.isDigit(c))
                break;
            res = res*10+(c-'0');
            if(res>Integer.MAX_VALUE){
                return neg?Integer.MIN_VALUE:Integer.MAX_VALUE;
            }
        }
        return neg?(int)res*-1:(int)res;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)