# Question

You are given a string num, representing a large integer. Return the largest-valued odd integer (as a string) that is a non-empty substring of num, or an empty string "" if no odd integer exists.

A substring is a contiguous sequence of characters within a string.



##### Example:

Input: num = "52"

Output: "5"

Explanation: The only non-empty substrings are "5", "2", and "52". "5" is the only odd number.



### Solve: [https://leetcode.com/problems/largest-odd-number-in-string/description/](https://leetcode.com/problems/largest-odd-number-in-string/description/)

***

# Optimal Solution
        

``` java
    public String largestOddNumber(String num) {
        for(int i=num.length()-1;i>=0;--i){
            int temp = (num.charAt(i)-'0');
            if(temp%2!=0){
                return num.substring(0,i+1);
            }
        }
        return "";
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)