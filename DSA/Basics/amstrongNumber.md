# Question

You are given a 3-digit number n, Find whether it is an Armstrong number or not.

An Armstrong number of three digits is a number such that the sum of the cubes of its digits is equal to the number itself. 371 is an Armstrong number since 33 + 73 + 13 = 371. 

 

##### Example 1:

Input: n = 153

Output: true

Explanation: 153 is an Armstrong number since 13 + 53 + 33 = 153.

### Solve: [https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1](https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1)

***

# Optimal Solution

``` java
    static boolean armstrongNumber(int n) {
        // code here
        int sum = 0;
        int temp =n;
        while(temp>0){
            int rem = temp%10;
            sum+=(rem*rem*rem);
            temp/=10;
        }
        if(sum==n)
            return true;
        return false;
    }
```

### Time Complexity: O(no of digits)
### Space Complexity: O(1)
