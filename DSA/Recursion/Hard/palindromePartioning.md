# Question  

Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.





##### Examples :

Input: s = "aab"

Output: [["a","a","b"],["aa","b"]]



### Solve: [https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)

*** 

# Optimal Solution 

``` java
    public List<List<String>> partition(String s) {
        List<List<String>> res = new ArrayList<>();
        List<String> curr = new ArrayList<>();
        findPalindrome(s,res,curr,0);
        return res;
    }

    void findPalindrome(String str,List<List<String>> res,List<String> curr, int idx){
        if(idx==str.length()){
            res.add(new ArrayList<>(curr));
            return ;
        }
        for(int i=idx;i<str.length();++i){
            String sub = str.substring(idx,i+1);
            if(isPalindrome(sub)){
                curr.add(sub);
                findPalindrome(str,res,curr,i+1);
                curr.remove(curr.size()-1);
            }
        }
    }
    boolean isPalindrome(String str){
        int start = 0,end = str.length()-1;
        while(start<end){
            if(str.charAt(start)!=str.charAt(end)){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
```