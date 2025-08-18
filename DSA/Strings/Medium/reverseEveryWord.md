# Question

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.


##### Example:

Input: s = "the sky is blue"

Output: "blue is sky the"


### Solve: [https://leetcode.com/problems/reverse-words-in-a-string/](https://leetcode.com/problems/reverse-words-in-a-string/)

***

# Optimal Solution
        

``` java
    public String reverseWords(String s) {
        s = s.trim();
        StringBuilder sb = new StringBuilder();
        int firstIndex = 0;
        for(int i=0;i<s.length();++i){
            if(s.charAt(i)==' '){
                sb.insert(0,s.substring(firstIndex,i));
                while(i<s.length()-1 && s.charAt(i+1)==' ')
                    i++;
                sb.insert(0," ");
                firstIndex=i+1;
            }
        }
        sb.insert(0,s.substring(firstIndex,s.length()));
        return sb.toString();
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)