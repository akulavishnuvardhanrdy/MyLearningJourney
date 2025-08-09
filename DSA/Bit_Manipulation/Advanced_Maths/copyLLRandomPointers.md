# Question

Given a number n. Find its unique prime factors in increasing order.

##### Example:

Input: n = 100

Output: [2, 5]

Explanation: Unique prime factors of 100 are 2 and 5.



### Solve: [https://www.geeksforgeeks.org/problems/prime-factors5052/1](https://www.geeksforgeeks.org/problems/prime-factors5052/1)
   


# Optimal Solution:  


``` java
    public static ArrayList<Integer> primeFac(int n) {
        // code here
        ArrayList<Integer> res = new ArrayList<>();
        for(int i=2;i*i<=n;++i){
            if(n%i==0)
                res.add(i);
            while(n%i==0){
                n = n/i;
            }
        }  
        if(n>1){
            res.add(n);
        }
        return res;
    }
```
### Time Complexity: O(root n)
### Space Complexity: O(logN)