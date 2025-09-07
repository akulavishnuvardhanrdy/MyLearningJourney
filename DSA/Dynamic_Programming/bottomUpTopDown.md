# Question

Geek is learning data structures, and he recently learned about the top-down and bottom-up dynamic programming approaches. Geek is having trouble telling them apart from one another.

When given an integer n, where n is based on a 0-based index, find the nth Fibonacci number.

Every ith number in the series equals the sum of the (i-1)th and (i-2)th numbers, where the first and second numbers are specified as 0 and 1, respectively.

For the given issue, code both top-down and bottom-up approaches.

Note : As the answer might be large, return the final answer modulo 109 + 7



##### Example:

Input:
n = 5

Output: 5

Explanation: 0,1,1,2,3,5 as we can see 5th number is 5.




### Solve: [https://www.geeksforgeeks.org/problems/introduction-to-dp/1](https://www.geeksforgeeks.org/problems/introduction-to-dp/1)
   


# Optimal Solution:  


``` java
    static long topDown(int n) {
        long arr[] = new long[n+1];
        for(int i=0;i<arr.length;++i) arr[i] = -1;
        return memorization(arr, n);
    }
    
    static long memorization(long[] arr,int n){
        if(n<=1)
            return n;
        if(arr[n]!=-1) return arr[n];
        long mod = (long)Math.pow(10,9)+7;
        arr[n] = (memorization(arr,n-1)+memorization(arr,n-2))%mod;
        return arr[n];
    }

    static long bottomUp(int n) {
        
        // code here
        long mod = (long)Math.pow(10,9)+7;
        long[] arr = new long[n+1];
        arr[0] = 0;
        arr[1] = 1;
        for(int i=2;i<=n;++i){
            arr[i] = (arr[i-1]+arr[i-2])%mod;
        }
        return arr[n];
    }
```
### Time Complexity: O(n)
### Space Complexity: O(n)