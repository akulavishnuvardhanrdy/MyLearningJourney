# Question  

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false. 



##### Examples :

Input: numCourses = 2, prerequisites = [[1,0]]

Output: true

Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.




### Solve: [https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

*** 

# Optimal Solution 

``` java
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adj = new ArrayList<>();
        boolean pathVis[] = new boolean[numCourses];
        boolean vis[] = new boolean[numCourses];
        for(int i=0;i<numCourses;++i){
            adj.add(new ArrayList<>());
        }
        for(int i=0;i<prerequisites.length;++i){
            adj.get(prerequisites[i][0]).add(prerequisites[i][1]);
        }
        for(int i=0;i<numCourses;++i){
            if(!vis[i]){
                if(dfs(adj,vis,pathVis,i))
                    return false;
            }
        }
        return true;
    }
    static boolean dfs(List<List<Integer>> adj,boolean vis[],boolean pathVis[],int node){
       vis[node] = true;
       pathVis[node] = true; 
       for(int curr:adj.get(node)){
           if(!vis[curr]){
               if(dfs(adj,vis,pathVis,curr))
                    return true;
           }
            else if(pathVis[curr])
                return true;
       }
       pathVis[node] = false;
       return false;
    }
```