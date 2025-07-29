# Question

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

 

##### Example:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]

Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

### Solve: [https://leetcode.com/problems/merge-intervals/](https://leetcode.com/problems/merge-intervals/)

***

# Optimal Solution


``` java
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals,(a,b)->a[0]-b[0]);
        List<int []> ls = new ArrayList<>();
        for(int i=0;i<intervals.length;++i){
            if(ls.size()!=0 && 
            ls.get(ls.size()-1)[1]>=intervals[i][0]){
                int last = ls.size()-1;
                int end = Math.max(ls.get(last)[1],intervals[i][1]);
                ls.get(last)[1] = end;
            }
            else{
                ls.add(new int[]{intervals[i][0],intervals[i][1]});
            }
        }
        return ls.toArray(new int[ls.size()][]);
    }
```

### Time Complexity: O(n*logn)+O(n)
### Space Complexity: O(2n)