# Question  

Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, check whether it contains any cycle or not.
The graph is represented as a 2D vector edges[][], where each entry edges[i] = [u, v] denotes an edge from verticex u to v.



##### Examples :

Input: V = 4, edges[][] = [[0, 1], [1, 2], [2, 0], [2, 3]]

Output: true

Explanation: The diagram clearly shows a cycle 0 → 1 → 2 → 0




### Solve: [https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)

*** 

# Optimal Solution 

``` java
    public boolean isCyclic(int V, int[][] edges) {
        // code here
        int indegree[] = new int[V];
        List<List<Integer>> adj = new ArrayList<>();
        ArrayDeque<Integer> q = new ArrayDeque<>();
        ArrayList<Integer> res = new ArrayList<>();
        for(int i=0;i<V;++i)
            adj.add(new ArrayList<>());
        for(int i=0;i<edges.length;++i){
            adj.get(edges[i][0]).add(edges[i][1]);
            indegree[edges[i][1]]++;
        }
        for(int i=0;i<V;++i){
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
        return res.size()==V?false:true;
    }
```