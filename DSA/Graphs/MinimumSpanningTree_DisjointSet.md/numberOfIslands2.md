# Question  

You have a 2D grid of ‘N’ rows and ‘M’ columns which are initially filled with water. You are given ‘Q’ queries each consisting of two integers ‘X’ and ‘Y’ and in each query operation, you have to turn the water at position (‘X’, ‘Y’) into a land. You are supposed to find the number of islands in the grid after each query.

An island is a group of lands surrounded by water horizontally, vertically, or diagonally.



##### Examples :

Sample Input 1:
2
3 3
4
0 0
0 1
1 2
2 1
4 5
4
1 1
0 1
3 3
3 4
Sample Output 1:
1 1 2 3
1 1 2 2
Explanation of Sample Output 1:
In test case 1, 

0.  000
    000
    000

1.  100
    000
    000

2.  110
    000
    000

 3. 110
    001
    000

 4. 110
    001
    100

So, the answer is 1, 1, 2, 3.

In test case 2,

0.  00000
    00000
    00000
    00000

1.  00000
    01000
    00000
    00000

2.  01000
    01000
    00000
    00000

 3. 01000
    01000
    00000
    00010

 4. 01000
    01000
    00000
    00011

So, the answer is 1, 1, 2, 2.



### Solve: [https://www.naukri.com/code360/problems/number-of-islands-ii_1266048?leftPanelTabValue=PROBLEM](https://www.naukri.com/code360/problems/number-of-islands-ii_1266048?leftPanelTabValue=PROBLEM)

*** 

# Optimal Solution 

``` java
public class Solution {
    public static int[] numOfIslandsII(int n, int m, int[][] queries) {
        // Write your code here.
        UnionFind ds = new UnionFind(n*m);
        int count = 0;
        boolean adj[][] = new boolean[n][m];
        int res[] = new int[queries.length];
        int del[] = new int[]{-1,0,1,0,-1};
        int k=0;
        for(int[] query:queries){
            int row = query[0],col = query[1];
            int idx = row*m+col;
            if(adj[row][col]){   
                res[k++] = count;
                continue;
            }
            count++;
            adj[row][col] = true;
            for(int i=1;i<del.length;++i){
                int delrow = row+del[i-1];
                int delcol = col+del[i];
                int curr = delrow*m+delcol;
                if(delrow>=0 && delcol>=0 && delrow<n && delcol<m && adj[delrow][delcol]){
                    if(ds.union(idx,curr))
                        count--;
                }
            }
            res[k++] = count;            
        }
        return res;
    }
}

class UnionFind{
    int par[],rank[];
    UnionFind(int n){
        par = new int[n];
        rank = new int[n];
        for(int i=0;i<n;++i){
            par[i] = i;
            rank[i] = 1;
        }
    }
    int find(int n){
        if(par[n]==n)
            return n;
        return par[n] = find(par[n]);
    }
    boolean union(int u,int v){
        int pu = find(u);
        int pv = find(v);
        if(pu==pv)
            return false;
        if(rank[pu]<rank[pv])
            par[pu] = pv;
        else if(rank[pu]>rank[pv])
            par[pv] = pu;
        else{
            par[pv] = pu;
            rank[pu]++;
        }
        return true;
    }
}
```