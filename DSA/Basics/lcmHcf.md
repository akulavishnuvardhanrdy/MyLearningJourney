# Question

Given two integers a and b, You have to compute their LCM and GCD and return an array containing their LCM and GCD.

 

##### Example 1:

Input: a = 5 , b = 10

Output: [10, 5]

Explanation: LCM of 5 and 10 is 10, while their GCD is 5.

### Solve: [https://www.geeksforgeeks.org/problems/lcm-and-gcd4516/1](https://www.geeksforgeeks.org/problems/lcm-and-gcd4516/1)

***

# Optimal Solution

``` java
    public static int[] lcmAndGcd(int a, int b) {
        // code here
        int res[] = new int[2];
        if(a<b) res[1]=hcf(b,a);
        else res[1] = hcf(a,b);
        res[0]=(a*b)/res[1];
        return res;
    }
    
    static int hcf(int a, int b){
        if(b==0) return a;
        return hcf(b,a%b);
    }
```

### Time Complexity: O(no of digits)
### Space Complexity: O(1)
