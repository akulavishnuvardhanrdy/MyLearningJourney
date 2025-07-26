# Question  
You are given 2 numbers n and m, the task is to find n√m (nth root of m). If the root is not integer then returns -1.

 

##### Example 1:

Input: n = 2, m = 9

Output: 3

Explanation: 32 = 9

### Solve: [https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1](https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1)

***   


# Optimal Solution*  
``` java
    public int nthRoot(int n, int m) {
        int low =0, high = m;
        while(low<=high){
            int mid = low+(high-low)/2;
            long temp = func(mid,n,m);
            if(temp == 1)
                return mid;
            if(temp == 0)
                low = mid +1;
            else
                high = mid -1;
        }
        return -1;
    }
    
    public int func(int base,int pow,int m){
        int temp = 1;
        for(int i=0;i<pow;++i){
            temp*= base;
            if(temp>m) return 2;
        }
        if(temp == m)
            return 1;
        return 0;
    }
```
### Time Complexity: O(N*logM)  
### Space Complexity: O(1) 