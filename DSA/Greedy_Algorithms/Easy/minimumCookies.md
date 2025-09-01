# Question

Given an infinite supply of each denomination of Indian currency { 1, 2, 5, 10, 20, 50, 100, 200, 500, 2000 } and a target value N.
Find the minimum number of coins and/or notes needed to make the change for Rs N. You must return the list containing the value of coins required. 



##### Example:

Input: N = 43

Output: 20 20 2 1

Explaination: 
Minimum number of coins and notes needed 
to make 43. 



### Solve: [https://www.geeksforgeeks.org/problems/-minimum-number-of-coins4426/1](https://www.geeksforgeeks.org/problems/-minimum-number-of-coins4426/1)

***

# Optimal Solution
        

``` java
    static List<Integer> minPartition(int N) {
        // code here
        int arr[] = new int[]{1,2,5,10,20,50,100,200,500,2000};
        List<Integer> ls = new ArrayList<Integer>();
        int pos = arr.length-1;
        while(pos>=0 && N>0){
            if(N>=arr[pos]){
                ls.add(arr[pos]);
                N-=arr[pos];
            }
            else{
                pos--;
            }
        }
        return ls;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)