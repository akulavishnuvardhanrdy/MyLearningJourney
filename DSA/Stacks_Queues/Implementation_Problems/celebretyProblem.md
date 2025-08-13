# Question

A celebrity is a person who is known to all but does not know anyone at a party. A party is being organized by some people. A square matrix mat[][] (n*n) is used to represent people at the party such that if an element of row i and column j is set to 1 it means ith person knows jth person. You need to return the index of the celebrity in the party, if the celebrity does not exist, return -1.

Note: Follow 0-based indexing.



##### Example:

Input: mat[][] = [[1, 1, 0], [0, 1, 0], [0, 1, 1]]

Output: 1

Explanation: 0th and 2nd person both know 1st person. Therefore, 1 is the celebrity person. 

### Solve: [https://www.geeksforgeeks.org/problems/the-celebrity-problem/1](https://www.geeksforgeeks.org/problems/the-celebrity-problem/1)
   


# Optimal Solution:  


``` java
    public int celebrity(int mat[][]) {
        int n = mat.length;
        int a = 0,b = n-1;
        while(a<b){
            if(mat[a][b]==1)
                a++;
            else
                b--;
        }
        for(int i=0;i<n;++i){
            if(i!=a && (mat[a][i]!=0 || mat[i][a]!=1))
                return -1;
        }
        return a;
    }
```
### Time Complexity: O(2*n)
### Space Complexity: O(1)