# Question  

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return the ordering of courses you should take to finish all courses. If there are many valid answers, return any of them. If it is impossible to finish all courses, return an empty array.



##### Examples :

Input: numCourses = 2, prerequisites = [[1,0]]

Output: [0,1]

Explanation: There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].




### Solve: [https://leetcode.com/problems/course-schedule-ii/](https://leetcode.com/problems/course-schedule-ii/)

*** 

# Optimal Solution 

``` java
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        int indegree[] = new int[numCourses];
        List<List<Integer>> adj = new ArrayList<>();
        ArrayDeque<Integer> q = new ArrayDeque<>();
        ArrayList<Integer> res = new ArrayList<>();
        for(int i=0;i<numCourses;++i)
            adj.add(new ArrayList<>());
        for(int i=0;i<prerequisites.length;++i){
            adj.get(prerequisites[i][1]).add(prerequisites[i][0]);
            indegree[prerequisites[i][0]]++;
        }
        for(int i=0;i<numCourses;++i){
            if(indegree[i]==0)
                q.addLast(i);
        }
        while(!q.isEmpty()){
            int node = q.pollFirst();
            for(int curr:adj.get(node)){
                indegree[curr]--;
                if(indegree[curr]==0){
                    q.addLast(curr);
                }
            }
            res.add(node);
        }
        if(res.size()!=numCourses) return new int[0];
        int arr[] = new int[res.size()];
        for(int i=0;i<res.size();++i){
            arr[i] = res.get(i);
        }
        return arr;
    }
```