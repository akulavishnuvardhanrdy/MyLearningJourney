# Question  

You are given an undirected graph consisting of V vertices and E edges represented by a list edges[][], along with an integer m. Your task is to determine whether it is possible to color the graph using at most m different colors such that no two adjacent vertices share the same color. Return true if the graph can be colored with at most m colors, otherwise return false.

Note: The graph is indexed with 0-based indexing.



##### Examples :

Input: V = 4, edges[][] = [[0, 1], [1, 3], [2, 3], [3, 0], [0, 2]], m = 3

Output: true

Explanation: It is possible to color the given graph using 3 colors, for example, one of the possible ways vertices can be colored as follows:

Vertex 0: Color 1
Vertex 1: Color 2
Vertex 2: Color 2
Vertex 3: Color 3



### Solve: [https://www.geeksforgeeks.org/problems/m-coloring-problem-1587115620/1](https://www.geeksforgeeks.org/problems/m-coloring-problem-1587115620/1)

*** 

# Optimal Solution 

``` java
    boolean graphColoring(int v, int[][] edges, int m) {
        // code here
        int color[] = new int[v];
        Arrays.fill(color,-1);
        return isPossible(v,edges,m,color,0);
    }
    boolean isPossible(int v,int[][] edges, int m, int color[],int idx){
        if(idx==v){
            return true;
        }
        for(int i=0;i<m;++i){
            if(isValidColor(edges,idx,i,color)){
                color[idx] = i;
                if(isPossible(v,edges,m,color,idx+1))
                    return true;
                color[idx] = -1;
            }
        }
        return false;
    }
    boolean isValidColor(int edges[][],int v,int c, int color[]){
        for(int i=0;i<edges.length;++i){
            if(edges[i][0]==v && color[edges[i][1]]==c)
                return false;
            if(edges[i][1]==v && color[edges[i][0]]==c)
                return false;
        }
        return true;
    }
```