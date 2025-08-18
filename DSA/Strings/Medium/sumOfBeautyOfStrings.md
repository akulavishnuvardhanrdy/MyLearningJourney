# Question

The beauty of a string is the difference in frequencies between the most frequent and least frequent characters.

For example, the beauty of "abaacc" is 3 - 1 = 2.
Given a string s, return the sum of beauty of all of its substrings.


##### Example:

Input: s = "aabcb"

Output: 5

Explanation: The substrings with non-zero beauty are ["aab","aabc","aabcb","abcb","bcb"], each with beauty equal to 1.



### Solve: [https://leetcode.com/problems/sum-of-beauty-of-all-substrings/](https://leetcode.com/problems/sum-of-beauty-of-all-substrings/)

***

# Optimal Solution
        

``` java
    public int beautySum(String s) {
        int sum = 0;
        for(int i=0;i<s.length();++i){
            int count[] = new int[26];
            for(int j=i;j<s.length();++j){
                int min = Integer.MAX_VALUE;
                int max = Integer.MIN_VALUE;
                count[s.charAt(j)-'a']++;
                for(int k: count){
                    if(k>0){
                        min = Math.min(min,k);
                        max = Math.max(max,k);
                    }
                }
                sum += (max - min);
            }
        }
        return sum;
    }
```

### Time Complexity: O(n^2*26)
### Space Complexity: O(26)