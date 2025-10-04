# Question  

Given a connected undirected graph containing V vertices, represented by a 2-d adjacency list adj[][], where each adj[i] represents the list of vertices connected to vertex i. Perform a Breadth First Search (BFS) traversal starting from vertex 0, visiting vertices from left to right according to the given adjacency list, and return a list containing the BFS traversal of the graph.

Note: Do traverse in the same order as they are in the given adjacency list.



##### Examples :

Input: adj[][] = [[2, 3, 1], [0], [0, 4], [0], [2]]

Output: [0, 2, 3, 1, 4]

Explanation: Starting from 0, the BFS traversal will follow these steps: 
Visit 0 → Output: 0 
Visit 2 (first neighbor of 0) → Output: 0, 2 
Visit 3 (next neighbor of 0) → Output: 0, 2, 3 
Visit 1 (next neighbor of 0) → Output: 0, 2, 3, 
Visit 4 (neighbor of 2) → Final Output: 0, 2, 3, 1, 4




### Solve: [https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1](https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

*** 

# Optimal Solution 

``` java
    public ArrayList<Integer> bfs(ArrayList<ArrayList<Integer>> adj) {
        // code here
        ArrayList<Integer> res = new ArrayList<>();
        ArrayDeque<Integer> q = new ArrayDeque<>();
        int[] visited = new int[adj.size()];
        q.addLast(0);
        visited[0] = 1;
        while(!q.isEmpty()){
            int curr = q.pollFirst();
            res.add(curr);
            ArrayList<Integer> temp = adj.get(curr);
            for(int i=0;i<temp.size();++i){
                if(visited[temp.get(i)]!=1){
                    q.addLast(temp.get(i));
                    visited[temp.get(i)]=1;
                }
            }
        }
        return res;
    }
```