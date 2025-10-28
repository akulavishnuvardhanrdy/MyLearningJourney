# Question  

You are given a network of n nodes, labeled from 1 to n. You are also given times, a list of travel times as directed edges times[i] = (ui, vi, wi), where ui is the source node, vi is the target node, and wi is the time it takes for a signal to travel from source to target.

We will send a signal from a given node k. Return the minimum time it takes for all the n nodes to receive the signal. If it is impossible for all the n nodes to receive the signal, return -1.



##### Examples :

Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2

Output: 2




### Solve: [https://leetcode.com/problems/network-delay-time/](https://leetcode.com/problems/network-delay-time/)

*** 

# Optimal Solution 

``` java
    public int networkDelayTime(int[][] times, int n, int k) {
        int res[] = new int[n+1];
        Arrays.fill(res,Integer.MAX_VALUE);
        List<List<Edge>> adj = new ArrayList<>();
        PriorityQueue<Pair> pq = new PriorityQueue<>(
            (a,b)->a.cost-b.cost
        );
        for(int i=0;i<n+1;++i){
            adj.add(new ArrayList<>());
        }
        for(int i=0;i<times.length;++i){
            adj.get(times[i][0]).add(new Edge(times[i][1],times[i][2]));
        }
        pq.add(new Pair(k,0));
        while(!pq.isEmpty()){
            Pair p = pq.poll();
            if(p.cost>res[p.node])
                continue;
            for(Edge curr:adj.get(p.node)){
                int resCost = p.cost+curr.cost;
                if(resCost<res[curr.des]){
                    res[curr.des] = resCost;
                    pq.add(new Pair(curr.des,resCost));
                }
            }
        }
        res[k] = 0;
        int min = Integer.MIN_VALUE;
        res[0] = -1;
        for(int i:res){
            if(i==Integer.MAX_VALUE)
                return -1;
            min = Math.max(min,i);
        }
        return min;
    }
    static class Edge{
        int des;
        int cost;
        Edge(int des,int cost){
            this.des = des;
            this.cost = cost;
        }
    }
    static class Pair{
        int node;
        int cost;
        Pair(int node,int cost){
            this.node = node;
            this.cost = cost;
        }
    }
```