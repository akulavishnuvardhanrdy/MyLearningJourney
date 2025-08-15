# Question

Given two strings s and t, return true if t is an anagram of s, and false otherwise.
 



##### Example:

Input: s = "anagram", t = "nagaram"

Output: true



### Solve: [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

***

# Optimal Solution
        

``` java
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
            return false;
        int count[] = new int[26];
        for(int i=0;i<s.length();++i){
            count[s.charAt(i)-'a']++;
        }   
        for(int i=0;i<t.length();++i){
            count[t.charAt(i)-'a']--;
        }
        for(int i=0;i<26;++i){
            if(count[i]!=0)
                return false;
        }
        return true;
    }
```

### Time Complexity: O(2n+26) 
### Space Complexity: O(26)