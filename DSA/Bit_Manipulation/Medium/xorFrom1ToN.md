# Question

You are given two integers L and R, your task is to find the XOR of elements of the range [L, R].

 

##### Example:

Input: 
L = 4, R = 8 

Output:
8 

Explanation:
4 ^ 5 ^ 6 ^ 7 ^ 8 = 8


### Solve: [https://www.geeksforgeeks.org/problems/find-xor-of-numbers-from-l-to-r/1](https://www.geeksforgeeks.org/problems/find-xor-of-numbers-from-l-to-r/1)
   


# Optimal Solution:  
``` java
    public static int findXOR(int l, int r) {
        return findXor(r)^findXor(l-1);
    }
    
    static int findXor(int n){
        switch(n%4){
            case 0:
                return n;
            case 1:
                return 1;
            case 2:
                return n+1;
            case 3:
                return 0;
        }
        return -1;
    }
```
### Time Complexity: O(1)  
### Space Complexity: O(1) 