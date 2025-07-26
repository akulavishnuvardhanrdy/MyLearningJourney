# Question  
Given a positive integer n, find the square root of n. If n is not a perfect square, then return the floor value.

Floor value of any number is the greatest Integer which is less than or equal to that number.

 

##### Example 1:

Input: n = 4

Output: 2

Explanation: Since, 4 is a perfect square, so its square root is 2

### Solve: [https://www.geeksforgeeks.org/problems/square-root/1](https://www.geeksforgeeks.org/problems/square-root/1)

***   


# Optimal Solution*  
``` java
    int floorSqrt(int n) {
        int low = 0, high = n;
        while(low<=high){
            int mid = low+(high-low)/2;
            long square = mid*mid;
            if(square<=n)
                low = mid+1;
            else
                high = mid-1;
        }
        return high;
    }
```
### Time Complexity: O(logN)  
### Space Complexity: O(1) 