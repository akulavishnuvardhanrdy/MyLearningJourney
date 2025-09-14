# Question  

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.


##### Examples :

Input: n = 3

Output: ["((()))","(()())","(())()","()(())","()()()"]

### Solve: [https://leetcode.com/problems/generate-parentheses/](https://leetcode.com/problems/generate-parentheses/)

*** 

# Optimal Solution 

``` java
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<String>();
        StringBuilder sb = new StringBuilder();
        backtrack(n,0,0,res,sb);
        return res;
    }
    public void backtrack(int n , int open,int close,List<String> res,StringBuilder sb){
        if(sb.length()==2*n){
            res.add(sb.toString());
            return;
        }
        if(open<n){
            sb.append("(");
            backtrack(n,open+1,close,res,sb);
            sb.setLength(sb.length()-1);
        }
        if(open>close){
            sb.append(")");
            backtrack(n,open,close+1,res,sb);
            sb.setLength(sb.length()-1);
        }
    }
```

### Time Complexity: O(4^N/root(n))  
### Space Complexity: O(Cn*n) 