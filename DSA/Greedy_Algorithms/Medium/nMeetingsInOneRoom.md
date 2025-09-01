# Question

You are given timings of n meetings in the form of (start[i], end[i]) where start[i] is the start time of meeting i and end[i] is the finish time of meeting i. Return the maximum number of meetings that can be accommodated in a single meeting room, when only one meeting can be held in the meeting room at a particular time. 

Note: The start time of one chosen meeting can't be equal to the end time of the other chosen meeting.



##### Example:

Input: start[] = [1, 3, 0, 5, 8, 5], end[] =  [2, 4, 6, 7, 9, 9]

Output: 4

Explanation: Maximum four meetings can be held with given start and end timings. The meetings are - (1, 2), (3, 4), (5,7) and (8,9)



### Solve: [https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)

***

# Optimal Solution
        

``` java
class Solution {
    // Function to find the maximum number of meetings that can
    // be performed in a meeting room.
    public int maxMeetings(int start[], int end[]) {
        // add your code here
        int n = start.length;
        Pair arr[] = new Pair[n];
        for(int i=0;i<n;++i){
            arr[i] = new Pair(start[i],end[i]);
        }
        Arrays.sort(arr,(a,b)->Integer.compare(a.end,b.end));
        int count = 1;
        Pair lastPair = arr[0];
        for(int i=1;i<n;++i){
            if(lastPair.end<arr[i].start){
                lastPair = arr[i];
                count++;
            }
        }
        return count;
    }
}
class Pair{
    int start;
    int end;
    Pair(int start,int end){
        this.start = start;
        this.end = end;
    }
}
```

### Time Complexity: O(n*logn+n)
### Space Complexity: O(n)