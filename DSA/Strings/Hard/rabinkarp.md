# Question

Given two strings text and pattern, find the first index where pattern exactly matches with any substring of text. 

Return -1 if pattern doesn't exist as a substring in text.




##### Example:

Input:
text = gffgfg
pattern = gfg

Output: 3
Explanation:  Considering 0-based indexing, substring of text from 3rd to last index is gfg.


### Solve: [https://www.geeksforgeeks.org/problems/index-of-the-first-occurrence-of-pattern-in-a-text/1](https://www.geeksforgeeks.org/problems/index-of-the-first-occurrence-of-pattern-in-a-text/1)

***

# Optimal Solution
        

``` java
    public int findMatching(String text, String pat) {
        int n = text.length();
        int m = pat.length();
        if(m>n) return -1;
        int base = 256, mod = Integer.MAX_VALUE;
        long targetHash = 0, calHash = 0, highPow = 1;
        for(int i=0;i<m-1;++i){
            highPow = (highPow*base)%mod;
        }
        for(int i=0;i<m;++i){
            targetHash = (targetHash*base + pat.charAt(i))%mod;
            calHash = (calHash*base + text.charAt(i))%mod;
        }
        for(int i=0;i<=n-m;++i){
            if(calHash==targetHash){
                if(text.substring(i,i+m).equals(pat))
                    return i;
            }
            if(i<n-m){
                calHash = (calHash-(text.charAt(i)*highPow) % mod+mod)%mod;
                calHash = (calHash*base+text.charAt(i+m))%mod;
            }
        }
        return -1;
    }
```

### Time Complexity: O(n+m)
### Space Complexity: O(1)