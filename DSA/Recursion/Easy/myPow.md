# Question  

Implement pow(x, n), which calculates x raised to the power n (i.e., xn).



##### Examples :

Input: x = 2.00000, n = 10

Output: 1024.00000



### Solve: [https://leetcode.com/problems/powx-n/](https://leetcode.com/problems/powx-n/)

*** 

# Optimal Solution 

``` java
    public double myPow(double x, int n) {
        long exp = n;
        if(exp<0){
            return 1/helper(x,-exp);
        }
        return helper(x,exp);
    }
    public double helper(double x,long n){
        if(n==0){
            return 1;
        }
        if(n%2==0){
            return helper(x*x,n/2);
        }
        else{
            return x*helper(x,n-1);
        }
    }
```

### Time Complexity: O(log*N)  
### Space Complexity: O(1) 