# Question

Given an integer array height[] where height[i] represents the height of the i-th stair, a frog starts from the first stair and wants to reach the top. From any stair i, the frog has two options: it can either jump to the (i+1)th stair or the (i+2)th stair. The cost of a jump is the absolute difference in height between the two stairs. Determine the minimum total cost required for the frog to reach the top.



##### Example:

Input: heights[] = [20, 30, 40, 20] 

Output: 20

Explanation:  Minimum cost is incurred when the frog jumps from stair 0 to 1 then 1 to 3:
jump from stair 0 to 1: cost = |30 - 20| = 10
jump from stair 1 to 3: cost = |20-30|  = 10
Total Cost = 10 + 10 = 20




### Solve: [https://www.geeksforgeeks.org/problems/geek-jump/1](https://www.geeksforgeeks.org/problems/geek-jump/1)
   


# Optimal Solution:  


``` java
    int minCost(int[] height) {
        int res[] = new int[height.length];
        Arrays.fill(res,-1);
        return func(height,res,height.length-1);
    }
    
    int func(int[] arr,int[] res, int pos){
        if(pos==0)
            return 0;
        if(res[pos]!=-1) 
            return res[pos];
        int cost1 = Math.abs(arr[pos]-arr[pos-1])+func(arr,res,pos-1);
        int cost2 = Integer.MAX_VALUE;
        if(pos>1)
            cost2 = Math.abs(arr[pos]-arr[pos-2])+func(arr,res,pos-2);
        res[pos] = Math.min(cost1,cost2);
        return res[pos];
    }
```
### Time Complexity: O(n)
### Space Complexity: O(2n)