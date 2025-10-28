# Question  

There is a directed graph of n nodes with each node labeled from 0 to n - 1. The graph is represented by a 0-indexed 2D integer array graph where graph[i] is an integer array of nodes adjacent to node i, meaning there is an edge from node i to each node in graph[i].

A node is a terminal node if there are no outgoing edges. A node is a safe node if every possible path starting from that node leads to a terminal node (or another safe node).

Return an array containing all the safe nodes of the graph. The answer should be sorted in ascending order.



##### Examples :

Input: graph = [[1,2],[2,3],[5],[0],[5],[],[]]

Output: [2,4,5,6]

Explanation: The given graph is shown above.
Nodes 5 and 6 are terminal nodes as there are no outgoing edges from either of them.
Every path starting at nodes 2, 4, 5, and 6 all lead to either node 5 or 6.




### Solve: [https://leetcode.com/problems/find-eventual-safe-states/description/](https://leetcode.com/problems/find-eventual-safe-states/description/)

*** 

# Optimal Solution 

``` java
    public List<Integer> eventualSafeNodes(int[][] graph) {
        int V = graph.length;
        int outdegree[] = new int[V];
        ArrayDeque<Integer> q = new ArrayDeque<>();
        List<List<Integer>> adj = new ArrayList<>();
        List<Integer> res = new ArrayList<>();
        for(int i=0;i<V;++i)
            adj.add(new ArrayList<>());
        for(int i=0;i<graph.length;++i){
            outdegree[i]=graph[i].length;
            if(outdegree[i]==0){
                q.addLast(i);
            }
            for(int j=0;j<graph[i].length;++j){
                adj.get(graph[i][j]).add(i);
            }
        }
        while(!q.isEmpty()){
            int node = q.pollFirst();
            res.add(node);
            for(int curr:adj.get(node)){
                outdegree[curr]--;
                if(outdegree[curr]==0)
                    q.addLast(curr);
            }
        }
        Collections.sort(res);
        return res;
    }
```