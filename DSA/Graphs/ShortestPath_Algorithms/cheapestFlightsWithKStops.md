# Question  

There are n cities connected by some number of flights. You are given an array flights where flights[i] = [fromi, toi, pricei] indicates that there is a flight from city fromi to city toi with cost pricei.

You are also given three integers src, dst, and k, return the cheapest price from src to dst with at most k stops. If there is no such route, return -1.



##### Examples :

Input: n = 4, flights = [[0,1,100],[1,2,100],[2,0,100],[1,3,600],[2,3,200]], src = 0, dst = 3, k = 1

Output: 700

Explanation:
The graph is shown above.
The optimal path with at most 1 stop from city 0 to 3 is marked in red and has cost 100 + 600 = 700.
Note that the path through cities [0,1,2,3] is cheaper but is invalid because it uses 2 stops.




### Solve: [https://leetcode.com/problems/cheapest-flights-within-k-stops/](https://leetcode.com/problems/cheapest-flights-within-k-stops/)

*** 

# Optimal Solution 

``` java
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        ArrayDeque<Pairs> q = new ArrayDeque<>();
        List<List<Route>> adj = new ArrayList<>();
        for(int i=0;i<n;++i)
            adj.add(new ArrayList<>());
        for(int i=0;i<flights.length;++i){
            adj.get(flights[i][0]).add(new Route(flights[i][1],flights[i][2]));
        }
        q.add(new Pairs(0,src,0));
        int res[] = new int[n];
        Arrays.fill(res,Integer.MAX_VALUE);
        res[src] = 0; 
        while(!q.isEmpty()){
            Pairs p = q.poll();
            for(Route curr:adj.get(p.node)){
                int rescost = p.cost+curr.cost;
                if(p.stops<=k){
                    if(rescost<res[curr.des]){
                        res[curr.des] = rescost;
                        q.add(new Pairs(p.stops+1,curr.des,rescost));
                    }
                }
            }
        }
        return res[dst]==Integer.MAX_VALUE?-1:res[dst];
    }
    static class Route{
        int des;
        int cost;
        public Route(int des,int cost){
            this.des = des;
            this.cost = cost;
        }
    }
    static class Pairs{
        int node;
        int stops;
        int cost;
        public Pairs(int stops,int node,int cost){
            this.node = node;
            this.stops = stops;
            this.cost = cost;
        }
    }
```