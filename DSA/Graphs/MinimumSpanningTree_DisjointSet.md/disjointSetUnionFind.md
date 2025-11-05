# Question  

You are given n elements numbered from 1 to n. Initially, each element is in its own group.

You need to process k queries. Each query is one of the following types:

UNION x z – Merge the groups that contain elements x and z. After this operation, both elements will belong to the same group.

FIND x – Output the ultimate representative of the group containing element x. The representative is the element that acts as the "leader" of the group.

Initially, every element is the leader of its own group.



##### Examples :

Input: n = 5, k = 4, queries[] = {{find 4}, {find 1}, {unionSet 3 1}, {find 3}}

Output: 4 1 1

Explanation:
1. The parent of 4 is 4. Hence the output is 4.
2. The parent of 1 is 1. Hence the output is 1.
3. After performing unionSet 3 1, parent of 3 becomes 1, since, parent of 1 is currently 1 itself.
4. The parent of 3 is now 1. Hence, the output is 1.




### Solve: [https://www.geeksforgeeks.org/problems/disjoint-set-union-find/1](https://www.geeksforgeeks.org/problems/disjoint-set-union-find/1)

*** 

# Optimal Solution 

``` java
    int find(int par[], int x) {
        // add code here.
        if(par[x]==x){
            return x;
        }
        return par[x] = par[find(par,par[x])]; //Path Compression
    }

    void unionSet(int par[], int x, int z) {
        // add code here.
        int parx = find(par,x);
        int parz = find(par,z);
        if(parx==parz)
            return ;
        par[parx] = par[parz];
    }
```