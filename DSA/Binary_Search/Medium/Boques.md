# Question  
You are given an integer array bloomDay, an integer m and an integer k.

You want to make m bouquets. To make a bouquet, you need to use k adjacent flowers from the garden.

The garden consists of n flowers, the ith flower will bloom in the bloomDay[i] and then can be used in exactly one bouquet.

Return the minimum number of days you need to wait to be able to make m bouquets from the garden. If it is impossible to make m bouquets return -1.
 

##### Example 1:

Input: bloomDay = [1,10,3,10,2], m = 3, k = 1

Output: 3

Explanation: Let us see what happened in the first three days. x means flower bloomed and _ means flower did not bloom in the garden.
We need 3 bouquets each should contain 1 flower.
After day 1: [x, _, _, _, _]   // we can only make one bouquet.
After day 2: [x, _, _, _, x]   // we can only make two bouquets.
After day 3: [x, _, x, _, x]   // we can make 3 bouquets. The answer is 3.

### Solve: [https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/)

***   


# Optimal Solution*  
``` java
    public int minDays(int[] bloomDay, int m, int k) {
        if((long)m*k>bloomDay.length)
            return -1;
        int low =0, high = maxElement(bloomDay);   
        while(low<=high){
            int mid = low+(high-low)/2;
            int noOfBoques = countBoques(bloomDay,k,mid);
            if(noOfBoques<m)
                low = mid+1;
            else 
                high = mid-1;
        }
        return low;
    }
    public int countBoques(int arr[], int k, int noOfDays){
        int n = 0;
        int temp = 0;
        for(int i=0;i<arr.length;++i){
            if(arr[i]<=noOfDays){
                temp++;
            }
            else{
                temp=0;
            }
            if(temp==k){
                n++;
                temp=0;
            }
        }
        return n;
    }

    public int maxElement(int bloomDay[]){
        int max = Integer.MIN_VALUE;
        for(int i:bloomDay){
            if(max<i) max =i;
        }
        return max;
    }
```
### Time Complexity: O(N*log(max no:of days))  
### Space Complexity: O(1) 