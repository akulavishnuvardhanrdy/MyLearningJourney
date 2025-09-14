# Question

Given a string s, find the length of the longest substring without duplicate characters.


##### Example 1:

Input: s = "abcabcbb"

Output: 3

Explanation: The answer is "abc", with the length of 3.



### Solve: [https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

***

# Optimal Solution

``` java
    public int lengthOfLongestSubstring(String s) {
        int temp[] = new int[256];
        Arrays.fill(temp,-1);
        int max=0,start =-1;
        for(int i=0;i<s.length();++i){
            char ch = s.charAt(i);
            if(temp[ch]>start){
                start = temp[ch];
            }
            else{
                max = Math.max(max,i-start);
            }
            temp[ch] = i;
        }
        return max;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)
