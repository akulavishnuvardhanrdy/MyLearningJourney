# Question  
A conveyor belt has packages that must be shipped from one port to another within days days.

The ith package on the conveyor belt has a weight of weights[i]. Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within days days
 

##### Example 1:

Input: weights = [1,2,3,4,5,6,7,8,9,10], days = 5

Output: 15

Explanation: A ship capacity of 15 is the minimum to ship all the packages in 5 days like this:
1st day: 1, 2, 3, 4, 5
2nd day: 6, 7
3rd day: 8
4th day: 9
5th day: 10

Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed.

### Solve: [https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

***   


# Optimal Solution*  
``` java
    public int shipWithinDays(int[] weights, int days) {
        int temp[] = maxSumElement(weights);
        int low = temp[0],high = temp[1];
        while(low<=high){
            int mid = low+(high-low)/2;
            int noOfdays = countDays(weights,mid);
            if(noOfdays>days){
                low = mid+1;
            }
            else{
                high = mid-1;
            }
        }
        return low;
    }

    public int countDays(int weights[],int mid){
        int days =0;
        int sum =0;
        for(int i: weights){
            sum+=i;
            if(sum>mid){
                days++;
                sum = i;
            }
        }
        return days+1;
    }

    public int[] maxSumElement(int nums[]){
        int max = Integer.MIN_VALUE;
        int sum =0;
        for(int i:nums){
            sum+=i;
            if(i>max)
                max =i;
        }
        return new int[]{max,sum};
    }
```
### Time Complexity: O(N+N*log(sumElement - maxElement))  
### Space Complexity: O(1) 