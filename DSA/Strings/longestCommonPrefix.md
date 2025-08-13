# Question

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".



##### Example:

Input: strs = ["flower","flow","flight"]

Output: "fl"



### Solve: [https://leetcode.com/problems/longest-common-prefix/](https://leetcode.com/problems/longest-common-prefix/)

***

# Optimal Solution
        

``` java
    public String longestCommonPrefix(String[] strs) {
        String prefix = strs[0];
        for(int i=0;i<strs.length;++i){
            while(strs[i].indexOf(prefix)!=0){
                System.out.println(prefix);
                prefix = prefix.substring(0,prefix.length()-1);
                if(prefix.isEmpty())
                    return prefix;
            }
        }
        return prefix;
    }
```

### Time Complexity: O(n+k) k-first string length
### Space Complexity: O(1)