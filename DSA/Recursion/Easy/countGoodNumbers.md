# Question  

A digit string is good if the digits (0-indexed) at even indices are even and the digits at odd indices are prime (2, 3, 5, or 7).

For example, "2582" is good because the digits (2 and 8) at even positions are even and the digits (5 and 2) at odd positions are prime. However, "3245" is not good because 3 is at an even index but is not even.
Given an integer n, return the total number of good digit strings of length n. Since the answer may be large, return it modulo 109 + 7.

A digit string is a string consisting of digits 0 through 9 that may contain leading zeros.



##### Examples :

Input: n = 1

Output: 5

Explanation: The good numbers of length 1 are "0", "2", "4", "6", "8".



### Solve: [https://leetcode.com/problems/count-good-numbers/](https://leetcode.com/problems/count-good-numbers/)

*** 

# Optimal Solution 

``` java
    private static final long mod = 1000000007;
    public int countGoodNumbers(long n) {
        long even = helper(5,(n+1)/2);
        long odd = helper(4,n/2);
        return (int)((even*odd)%mod);
    }
    public long helper(long x,long n){
        if(n==0){
            return 1;
        }
        if(n%2==0){
            return helper((x*x)%mod,n/2)%mod;
        }
        else{
            return ((x%mod)*helper(x,n-1))%mod;
        }
    }
```

### Time Complexity: O(log*N)  
### Space Complexity: O(1) 