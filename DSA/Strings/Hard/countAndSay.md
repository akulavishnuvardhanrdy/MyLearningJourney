# Question

The count-and-say sequence is a sequence of digit strings defined by the recursive formula:

countAndSay(1) = "1"
countAndSay(n) is the run-length encoding of countAndSay(n - 1).
Run-length encoding (RLE) is a string compression method that works by replacing consecutive identical characters (repeated 2 or more times) with the concatenation of the character and the number marking the count of the characters (length of the run). For example, to compress the string "3322251" we replace "33" with "23", replace "222" with "32", replace "5" with "15" and replace "1" with "11". Thus the compressed string becomes "23321511".

Given a positive integer n, return the nth element of the count-and-say sequence.




##### Example:

Input: n = 4

Output: "1211"


### Solve: [https://leetcode.com/problems/count-and-say/](https://leetcode.com/problems/count-and-say/)

***

# Optimal Solution
        

``` java
    public String countAndSay(int num) {
        if(num==1)
            return "1";
        String s = countAndSay(num-1);
        StringBuilder sb = new StringBuilder();
        for(int i=0;i<s.length();++i){
            char ch = s.charAt(i);
            int count = 1;
            while(i<s.length()-1 && ch==s.charAt(i+1)){
                count++;
                i++;
            }
            sb.append(count);
            sb.append(ch);
        }
        return sb.toString();
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)