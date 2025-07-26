# Question  
Dilpreet wants to paint his dog's home that has n boards with different lengths. The length of ith board is given by arr[i] where arr[] is an array of n integers. He hired k painters for this work and each painter takes 1 unit time to paint 1 unit of the board.

Return the minimum time to get this job done if all painters start together with the constraint that any painter will only paint continuous boards, say boards numbered [2,3,4] or only board [1] or nothing but not boards [2,4,5].
 

##### Example 1:

Input: arr[] = [5, 10, 30, 20, 15], k = 3

Output: 35

Explanation: The most optimal way will be: Painter 1 allocation : [5,10], Painter 2 allocation : [30], Painter 3 allocation : [20,15], Job will be done when all painters finish i.e. at time = max(5+10, 30, 20+15) = 35


### Solve: [https://www.geeksforgeeks.org/problems/the-painters-partition-problem1535/1](https://www.geeksforgeeks.org/problems/the-painters-partition-problem1535/1)

***   


# Optimal Solution*  
``` java
    public int minTime(int[] arr, int k) {
        // code here
        int temp[] = MaxTotal(arr);
        int low = temp[0],high = temp[1];
        while(low<=high){
            int mid = low+(high-low)/2;
            if(isPossible(arr,k,mid))
                high = mid-1;
            else
                low = mid+1;
        }
        return low;
    }
    
    public boolean isPossible(int arr[], int k, int mid){
        int painters=1;
        int currSum =0;
        for(int i:arr){
            if(currSum+i>mid){
                painters++;
                currSum = i;
                if(painters>k) return false;
            }
            else
                currSum+=i;
        }
        return true;
    }
    
    public int[] MaxTotal(int arr[]){
        int max = Integer.MIN_VALUE,sum=0;
        for(int i:arr){
            sum+=i;
            if(i>max) 
                max=i;
        }
        return new int[]{max,sum};
    }
```
### Time Complexity: O(N*log(sumElements - maxElement))  
### Space Complexity: O(1) 