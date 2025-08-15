# Question

Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.



##### Example:

Input: s = "egg", t = "add"

Output: true

Explanation:

The strings s and t can be made identical by:

Mapping 'e' to 'a'.
Mapping 'g' to 'd'.



### Solve: [https://leetcode.com/problems/isomorphic-strings/](https://leetcode.com/problems/isomorphic-strings/)

***

# Optimal Solution
        

``` java
    public boolean isIsomorphic(String s, String t) {
        char a[] = new char[128];
        char b[] = new char[128];
        for(int i=0; i<s.length();++i){
            char c1 = s.charAt(i);
            char c2 = t.charAt(i);
            if(a[c1]!=0 && a[c1]!=c2)
                return false;
            if(b[c2]!=0 && b[c2]!=c1)
                return false;
            a[c1] = c2;
            b[c2] = c1;
        }
        return true;
    }
```

### Time Complexity: O(n) 
### Space Complexity: O(128+128) ~ O(1)