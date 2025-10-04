# Question  

Geek is going for a training program for n days. He can perform any of these activities: Running, Fighting, and Learning Practice. Each activity has some point on each day. As Geek wants to improve all his skills, he can't do the same activity on two consecutive days. Given a 2D array arr[][] of size n where arr[i][0], arr[i][1], and arr[i][2] represent the merit points for Running, Fighting, and Learning on the i-th day, determine the maximum total merit points Geek can achieve .



##### Examples :

Input: arr[]= [[1, 2, 5], [3, 1, 1], [3, 3, 3]]

Output: 11

Explanation: Geek will learn a new move and earn 5 point then on second day he will do running and earn 3 point and on third day he will do fighting and earn 3 points so, maximum merit point will be 11.



### Solve: [https://www.geeksforgeeks.org/problems/geeks-training/1](https://www.geeksforgeeks.org/problems/geeks-training/1)

*** 

# Optimal Solution 

``` java
    public int maximumPoints(int arr[][]) {
        // code here
        int dp[][] = new int[arr.length][];
        int n = arr.length;
        for(int i=0;i<arr.length;++i){
            dp[i] = new int[4];
            Arrays.fill(dp[i],-1);
        }
        dp[0][0] = Math.max(arr[0][1],arr[0][2]);
        dp[0][1] = Math.max(arr[0][0],arr[0][2]);
        dp[0][2] = Math.max(arr[0][0],arr[0][1]);
        dp[0][3] = Math.max(arr[0][0],Math.max(arr[0][1],arr[0][2]));
        for(int idx=1;idx<n;++idx){
            for(int last=0;last<4;++last){
                int max = 0;
                for(int task=0;task<3;++task){
                    if(task!=last){
                        int points = arr[idx][task]+dp[idx-1][task];
                        max = Math.max(points,max);
                    }
                }
                dp[idx][last] = max; 
            }
        }
        return dp[n-1][3];
    }
```