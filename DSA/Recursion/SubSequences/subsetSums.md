# Question  

Given a array arr of integers, return the sums of all subsets in the list.  Return the sums in any order.



##### Examples :

Input: arr[] = [2, 3]

Output: [0, 2, 3, 5]

Explanation: When no elements are taken then Sum = 0. When only 2 is taken then Sum = 2. When only 3 is taken then Sum = 3. When elements 2 and 3 are taken then Sum = 2+3 = 5.



### Solve: [https://www.geeksforgeeks.org/problems/subset-sums2234/1](https://www.geeksforgeeks.org/problems/subset-sums2234/1)

*** 

# Optimal Solution 

``` java
    public ArrayList<Integer> subsetSums(int[] arr) {
        // code here
        ArrayList<Integer> res = new ArrayList<>();
        findSum(arr,res,0,0);
        return res;
    }
    public void findSum(int arr[],ArrayList<Integer> res,int sum,int idx){
        if(idx==arr.length){
            res.add(sum);
            return ;
        }
        findSum(arr,res,sum+arr[idx],idx+1);
        findSum(arr,res,sum,idx+1);
    }
```