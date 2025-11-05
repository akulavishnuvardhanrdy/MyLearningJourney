# Question  

Given start, end and an array arr of n numbers. At each step, start is multiplied with any number in the array and then mod operation with 100000 is done to get the new start.

Your task is to find the minimum steps in which end can be achieved starting from start. If it is not possible to reach end, then return -1.



##### Examples :

Input:
arr[] = {2, 5, 7}
start = 3, end = 30

Output:
2

Explanation:
Step 1: 3*2 = 6 % 100000 = 6 
Step 2: 6*5 = 30 % 100000 = 30




### Solve: [https://www.geeksforgeeks.org/problems/minimum-multiplications-to-reach-end/1](https://www.geeksforgeeks.org/problems/minimum-multiplications-to-reach-end/1)

*** 

# Optimal Solution 

``` java
    int minimumMultiplications(int[] arr, int start, int end) {
        // Your code here
        int res[] = new int[100000];
        int mod = (int)1e5;
        Arrays.fill(res,Integer.MAX_VALUE);
        res[start] = 0;
        ArrayDeque<Pair> q = new ArrayDeque<>();
        q.add(new Pair(start,0));
        while(!q.isEmpty()){
            Pair p = q.poll();
            if(p.num==end)
                return p.steps;
            if(p.steps>res[p.num])
                continue;
            for(int curr:arr){
                int newnum = (int)((p.num*1L*curr)%mod);
                if(p.steps+1<res[newnum]){
                    q.add(new Pair(newnum,p.steps+1));
                    res[newnum] = p.steps+1;
                }
            }
        }
        return -1;
    }
    static class Pair{
        int num;
        int steps;
        Pair(int num,int steps){
            this.num = num;
            this.steps = steps;
        }
    }
```