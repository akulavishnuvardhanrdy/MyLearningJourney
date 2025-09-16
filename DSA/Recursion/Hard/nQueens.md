# Question  

The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.

Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.



##### Examples :

Input: n = 4

Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]

Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above



### Solve: [https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/)

*** 

# Optimal Solution 

``` java
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> res = new ArrayList<>();
        List<String> curr = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        boolean diag1[] = new boolean[2*n];
        boolean diag2[] = new boolean[2*n];
        boolean col[] = new boolean[n];
        for(int i=0;i<n;++i){
            sb.append('.');
        }
        findCombinations(res,curr,sb,n,0,col,diag1,diag2);
        return res;
    }
    void findCombinations(List<List<String>> res,List<String> curr,StringBuilder sb,int n, int idx,boolean col[],boolean diag1[], boolean diag2[]){
        if(idx==n){
            res.add(new ArrayList(curr));
            return ;
        }
        for(int y=0;y<n;++y){
            if(valid(col,diag1,diag2,idx,y,n)){
                diag1[idx-y+n-1] = true;
                diag2[idx+y] = true;
                col[y] = true;
                sb.setCharAt(y,'Q');
                curr.add(sb.toString());
                sb.setCharAt(y,'.');
                findCombinations(res,curr,sb,n,idx+1,col,diag1,diag2);
                curr.remove(curr.size()-1);
                diag1[idx-y+n-1] = false;
                diag2[idx+y] = false;
                col[y] = false;
            }
        }
    }

    public boolean valid(boolean col[],boolean diag1[], boolean diag2[],int x,int y,int n){
        if(col[y])
            return false;
        if(diag1[x-y+n-1])
            return false;
        if(diag2[x+y])
            return false;
        return true;
    }
```