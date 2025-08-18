# Question

You are given a string consisting of lowercase characters and an integer k, You have to count all possible substrings that have exactly k distinct characters. 



##### Example:

Input: s = "abc", k = 2

Output: 2

Explanation: Possible substrings are ["ab", "bc"]



### Solve: [https://www.geeksforgeeks.org/problems/count-number-of-substrings4528/1](https://www.geeksforgeeks.org/problems/count-number-of-substrings4528/1)

***

# Optimal Solution
        

``` java
    int countSubstr(String s, int k) {
        if(k>s.length())
            return 0;
        return atMost(s,k)-atMost(s,k-1);
    }
    
    int atMost(String s, int k){
        int left = 0,n = s.length();
        Map<Character,Integer> map = new HashMap<>();
        int count = 0;
        for(int right=0;right<n;++right){
            char ch = s.charAt(right);
            map.put(ch,map.getOrDefault(ch,0)+1);
            while(map.size()>k){
                char lch = s.charAt(left);
                map.put(lch,map.get(lch)-1);
                if(map.get(lch)==0)
                    map.remove(lch);
                left++;
            }
            count+=right-left+1;
        }
        return count;
    }
```

### Time Complexity: O(4*n)
### Space Complexity: O(k)