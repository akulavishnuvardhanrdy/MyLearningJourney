# Question

Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:
 

##### Example:

Input: numRows = 5

Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

### Solve: [https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

***

# Optimal Solution


``` java
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
        for(int i=1;i<=numRows;++i){
            res.add(getRow(i));
        } 
        return res;
    }
    List<Integer> getRow(int row){
        List<Integer> ls = new ArrayList<Integer>();
        int num =1;
        ls.add(num);
        for(int i=1;i<row;++i){
            num*=(row-i);
            num/=i;
            ls.add(num);
        }
        return ls;
    }
```

### Time Complexity: O(n^2)
### Space Complexity: O(n^2)