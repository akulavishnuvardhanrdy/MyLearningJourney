# Question

Given a pair of strings s1 and s2 of equal lengths, your task is to find which of the two strings has more distinct subsequences. If both strings have the same number of distinct subsequences, return s1.


##### Example:

Input: s1 = "gfg", s2 = "ggg"

Output: "gfg"

Explanation: "gfg" have 6 distinct subsequences whereas "ggg" have 3 distinct subsequences.


### Solve: [https://www.geeksforgeeks.org/problems/better-string/1](https://www.geeksforgeeks.org/problems/better-string/1)
   


# Reccursive Solution(TLE):  
``` java
    public static String betterString(String s1, String s2) {
        // Code here
        Set<String> res1 = new HashSet<String>();
        Set<String> res2 = new HashSet<String>();
        StringBuilder sb = new StringBuilder();
        distinctSequence(s1,res1,sb,0);
        sb.setLength(0);
        distinctSequence(s2,res2,sb,0);
        if(res1.size()<res2.size())
            return s2;
        return s1;
    }
    public static void distinctSequence(String s,Set<String> set,StringBuilder sb,int idx){
        if(idx==s.length()){
            set.add(new String(sb));
            return;
        }
        sb.append(s.charAt(idx));
        distinctSequence(s,set,sb,idx+1);
        sb.setLength(sb.length()-1);
        distinctSequence(s,set,sb,idx+1);
    }
```
### Time Complexity: O(2^n *n)  
### Space Complexity: O(n) 


# Optimal Solution(DP):  
``` java
    public static String betterString(String s1, String s2) {
        // Code here
        int n1 = s1.length();
        int n2 = s2.length();
        int res1[] = new int[n1+1];
        int res2[] = new int[n2+1];
        findDistinct(s1,res1);
        findDistinct(s2,res2);
        
        if(res1[n1]<res2[n2])
            return s2;
        return s1;
    }
    
    static void findDistinct(String s,int res[]){
        res[0] = 1;
        int last[] = new int[256];
        Arrays.fill(last,-1);
        
        for(int i=0;i<s.length();++i){
            char c = s.charAt(i);
            int sub = 0;
            if(last[c]!=-1){
                sub = res[last[c]];
            }
            res[i+1] = (2*res[i])-sub;
            last[c] = i;
        }
    }
```
### Time Complexity: O(n)  
### Space Complexity: O(n) 