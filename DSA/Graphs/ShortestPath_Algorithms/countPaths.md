# Question  

You are in a city that consists of n intersections numbered from 0 to n - 1 with bi-directional roads between some intersections. The inputs are generated such that you can reach any intersection from any other intersection and that there is at most one road between any two intersections.

You are given an integer n and a 2D integer array roads where roads[i] = [ui, vi, timei] means that there is a road between intersections ui and vi that takes timei minutes to travel. You want to know in how many ways you can travel from intersection 0 to intersection n - 1 in the shortest amount of time.

Return the number of ways you can arrive at your destination in the shortest amount of time. Since the answer may be large, return it modulo 109 + 7.



##### Examples :

Input: n = 7, roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
Output: 4
Explanation: The shortest amount of time it takes to go from intersection 0 to intersection 6 is 7 minutes.
The four ways to get there in 7 minutes are:
- 0 ➝ 6
- 0 ➝ 4 ➝ 6
- 0 ➝ 1 ➝ 2 ➝ 5 ➝ 6
- 0 ➝ 1 ➝ 3 ➝ 5 ➝ 6




### Solve: [https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/)

*** 

# Optimal Solution 

``` java
    public int countPaths(int n, int[][] roads) {
        PriorityQueue<Pairs> pq = new PriorityQueue<>(
            (a,b)->Long.compare(a.dis,b.dis)
        );
        long ways[] = new long[n];
        ways[0] = 1;
        int mod = (int)1e9+7; 
        List<List<Edge>> adj = new ArrayList<>();
        long res[] = new long[n];
        Arrays.fill(res,Long.MAX_VALUE);
        res[0] = 0;
        for(int i=0;i<n;++i)
            adj.add(new ArrayList<>());
        for(int road[]:roads){
            adj.get(road[0]).add(new Edge(road[1],road[2]));
            adj.get(road[1]).add(new Edge(road[0],road[2]));
        }
        pq.add(new Pairs(0,0));
        while(!pq.isEmpty()){
            Pairs p = pq.poll();
            if(p.dis>res[p.node])
                continue;
            for(Edge curr:adj.get(p.node)){
                long rescost = p.dis+curr.cost;
                if(rescost<res[curr.des]){
                    res[curr.des] = rescost;
                    ways[curr.des] = ways[p.node];
                    pq.add(new Pairs(curr.des,rescost));
                }
                else if(rescost==res[curr.des]){
                    ways[curr.des] = (ways[p.node]+ways[curr.des])%mod;
                }
            }
        }
        return (int)ways[n-1];
    }
    static class Pairs{
        int node;
        long dis;
        public Pairs(int node,long dis){
            this.node = node;
            this.dis = dis;
        }
    }
    static class Edge{
        int des;
        int cost;
        public Edge(int des,int cost){
            this.des = des;
            this.cost = cost;
        }
    }
```