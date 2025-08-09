# Question

Given an integer n, print all the divisors of N in the ascending order.

##### Example:

Input : n = 20

Output: 1 2 4 5 10 20

Explanation: 20 is completely divisible by 1, 2, 4, 5, 10 and 20.



### Solve: [https://www.geeksforgeeks.org/problems/all-divisors-of-a-number/1](https://www.geeksforgeeks.org/problems/all-divisors-of-a-number/1)
   


# Optimal Solution:  


``` java
    public static void print_divisors(int n) {
        // code here
        Stack<Integer> st = new Stack<>();
        for(int i=1;i*i<=n;++i){
            if(n%i==0){
                System.out.print(i+" ");
                if(i!=(n/i))
                    st.add(n/i);
            }
        }
        while(!st.isEmpty()){
            System.out.print(st.pop()+" ");
        }
    }
```
### Time Complexity: O(root n)
### Space Complexity: O(root n)