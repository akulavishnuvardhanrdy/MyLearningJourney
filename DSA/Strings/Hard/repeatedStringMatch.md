# Question

Given two strings a and b, return the minimum number of times you should repeat string a so that string b is a substring of it. If it is impossible for b​​​​​​ to be a substring of a after repeating it, return -1.

Notice: string "abc" repeated 0 times is "", repeated 1 time is "abc" and repeated 2 times is "abcabc".



##### Example:

Input: a = "abcd", b = "cdabcdab"
Output: 3
Explanation: We return 3 because by repeating a three times "abcdabcdabcd", b is a substring of it.



### Solve: [https://leetcode.com/problems/repeated-string-match/](https://leetcode.com/problems/repeated-string-match/)

***

# Optimal Solution
        

``` java
    public int repeatedStringMatch(String a, String b) {
        StringBuilder sb = new StringBuilder(a);
        int count = 1;
        while(sb.length()<b.length()){
            sb.append(a);
            count++;
        }
        if(rabinKrap(sb.toString(),b)!=-1) return count;
        sb.append(a);
        if(rabinKrap(sb.toString(),b)!=-1) return count+1;
        return -1;
    }

    public int rabinKrap(String text, String pat) {
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