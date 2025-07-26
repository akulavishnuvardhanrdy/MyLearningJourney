# Question  
You are given an array with unique elements of stalls[], which denote the position of a stall. You are also given an integer k which denotes the number of aggressive cows. Your task is to assign stalls to k cows such that the minimum distance between any two of them is the maximum possible.
 

##### Example 1:

Input: stalls[] = [1, 2, 4, 8, 9], k = 3

Output: 3

Explanation: The first cow can be placed at stalls[0], 
the second cow can be placed at stalls[2] and 
the third cow can be placed at stalls[3]. 
The minimum distance between cows, in this case, is 3, which also is the largest among all possible ways.

### Solve: [https://www.geeksforgeeks.org/problems/aggressive-cows/0](https://www.geeksforgeeks.org/problems/aggressive-cows/0)

***   


# Optimal Solution*  
``` java
    public static int aggressiveCows(int[] stalls, int k) {
        Arrays.sort(stalls);
        int low = 1, high = stalls[stalls.length-1];
        while(low<=high){
            int mid = low+(high-low)/2;
            int noOfCows = findCows(stalls,mid);
            if(noOfCows<k)
                high = mid-1;
            else
                low = mid+1;
        }
        return high;
    }
    static int findCows(int arr[], int mid){
        int count=1,lastPlaced=arr[0];
        for(int i=1;i<arr.length;++i){
            if(arr[i]-lastPlaced>=mid){
                count++;
                lastPlaced = arr[i];
            }
        }
        return count;
    }
```
### Time Complexity: O(NlogN)+O(N*log(maxElement))  
### Space Complexity: O(1) 