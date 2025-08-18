# Question

Given a string s, return the longest palindromic substring in s.



##### Example:

Input: s = "babad"

Output: "bab"

Explanation: "aba" is also a valid answer.



### Solve: [https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/)

***

# Optimal Solution
        

``` java
    public String longestPalindrome(String s) {
        if(s==null || s.length()==0)
            return "";
        int right = 0, left = 0;
        for(int i=0;i<s.length();++i){
            int len1 = maxLength(s,i,i);
            int len2 = maxLength(s,i,i+1);
            int maxLen = Math.max(len1,len2);
            if(maxLen>right-left+1){
                right = i+(maxLen)/2;
                left = i-(maxLen-1)/2;
            }
        }
        return s.substring(left,right+1);
    }
    public int maxLength(String s, int left,int right){
        while(left>=0 && right<s.length() && s.charAt(left)==s.charAt(right)){
            left--;
            right++;
        }
        return right-left-1;
    }
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)