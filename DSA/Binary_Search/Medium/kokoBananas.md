# Question  
Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.
 

##### Example 1:

Input: piles = [3,6,7,11], h = 8

Output: 4

### Solve: [https://leetcode.com/problems/koko-eating-bananas/description/](https://leetcode.com/problems/koko-eating-bananas/description/)

***   


# Optimal Solution*  
``` java
    public int minEatingSpeed(int[] piles, int h) {
        int low = 1, high = maxElement(piles);
        while(low<=high){
            int mid = low+(high-low)/2;
            long hoursReq = calculateHours(piles,mid); 
            if(hoursReq>h)
                low = mid+1;
            else 
                high = mid-1;
        }
        return low;
    }

    public long calculateHours(int piles[], int k){
        long hours = 0;
        for(int i : piles){
            hours += (i+k-1)/k;
        }
        return hours;
    }
    public int maxElement(int piles[]){
        int max = Integer.MIN_VALUE;
        for(int i :piles){
            if(i>max)
                max = i;
        }
        return max;
    }
```
### Time Complexity: O(N+N*log(maxElement))  
### Space Complexity: O(1) 