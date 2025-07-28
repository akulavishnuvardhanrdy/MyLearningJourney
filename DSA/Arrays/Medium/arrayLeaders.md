# Question

You are given an array arr of positive integers. Your task is to find all the leaders in the array. An element is considered a leader if it is greater than or equal to all elements to its right. The rightmost element is always a leader.
 

##### Example:

Input: arr = [16, 17, 4, 3, 5, 2]

Output: [17, 5, 2]

Explanation: Note that there is nothing greater on the right side of 17, 5 and, 2.

### Solve: [https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1)

***

# Optimal Solution


``` java
    static ArrayList<Integer> leaders(int arr[]) {
        // code here
        int n = arr.length;
        ArrayList<Integer> ls = new ArrayList<>();
        int max = arr[n-1];
        for(int i=n-1;i>=0;--i){
            max = Math.max(max,arr[i]);
            if(arr[i]>=max)
                ls.add(0,arr[i]);
        }
        return ls;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(n)