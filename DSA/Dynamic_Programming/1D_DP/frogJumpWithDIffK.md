# Question

Given an array arr[] of size n, where arr[i] denotes the height of ith stone. Geek starts from stone 0 and from stone i, he can jump to stones i + 1, i + 2, … i + k. The cost for jumping from stone i to stone j is abs(arr[i] – arr[j]). Find the minimum cost for Geek to reach the last stone.


##### Example:

Input: k = 3, arr[]= [10, 30, 40, 50, 20]

Output: 30

Explanation: Geek will follow the path 1->2->5, the total cost would be |10-30| + |30-20| = 30, which is minimum.




### Solve: [https://www.geeksforgeeks.org/problems/minimal-cost/1](https://www.geeksforgeeks.org/problems/minimal-cost/1)
   


# Optimal Solution:  


``` java
    public int minimizeCost(int k, int arr[]) {
        int res[] = new int[arr.length];
        for(int pos=1;pos<arr.length;++pos){
            int cost = Integer.MAX_VALUE;
            for(int j=1;j<=k;++j){
                if(pos-j<0)
                    break;
                int temp = Math.abs(arr[pos]-arr[pos-j])+res[pos-j];
                cost = Math.min(cost,temp);
            }
            res[pos] = cost;
        }
        return res[res.length-1];
    }
```
### Time Complexity: O(n*k)
### Space Complexity: O(n)