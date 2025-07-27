# Question  
We have a horizontal number line. On that number line, we have gas stations at positions stations[0], stations[1], ..., stations[n-1], where n is the size of the stations array. Now, we add k more gas stations so that d, the maximum distance between adjacent gas stations, is minimized. We have to find the smallest possible value of d. Find the answer exactly to 2 decimal places.
Note: stations is in a strictly increasing order.
 

##### Example 1:

Input:
n = 10
stations[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
k = 9

Output: 0.50

Explanation: Each of the 9 stations can be added mid way between all the existing adjacent stations.

### Solve: [https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1](https://www.geeksforgeeks.org/problems/minimize-max-distance-to-gas-station/1)

***   


# Optimal Solution*  
``` java
class Solution {
    public static double findSmallestMaxDist(int stations[], int k) {
        // code here
        int n = stations.length;
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b)->Double.compare(b.maxDist(),a.maxDist()));
        for(int i=1;i<n;++i)
            pq.add(new Pair(stations[i]-stations[i-1],1));
        for(int i=0;i<k;++i){
            Pair pop = pq.poll();
            pop.parts++;
            pq.add(pop);
        }
        return (pq.peek().maxDist()*100.0)/100.0;
    }
}

class Pair {
    double dist;
    int parts;

    Pair(double dist, int parts) {
        this.dist = Math.round(dist * 100.0) / 100.0;
        this.parts = parts;
    }
    
    double maxDist(){
        return dist/parts;
    }
}
```
### Time Complexity: O(NlogN)+O(K*logN)  
### Space Complexity: O(N+K) 