# Question

Given an array arr[ ] of n positive integers, the task is to find the greatest element on the left of every element in the array which is strictly smaller than itself, if this element does not exist for an index print "-1".
 

##### Example:

Input: n = 5, arr[] = [2, 3, 4, 5, 1]

Output: -1 2 3 4 -1

Explanation:
Greatest element on the left of 3 smaller 
than itself is 2, for 4 it is 3 and for 5 
it is 1. Since 2 is the first element and 
no element on its left is present, so it's 
greatest smaller element will be -1 and for 
1 no element smaller than itself is present 
on its left, so it's greatest smaller element 
is -1.



### Solve: [https://www.geeksforgeeks.org/problems/smaller-on-left20360700/1](https://www.geeksforgeeks.org/problems/smaller-on-left20360700/1)

***

# Optimal Solution


``` java
    public static int[] Smallestonleft(int arr[], int n) {
        // Complete the function
        TreeSet<Integer> ts = new TreeSet<>();
        int res[] = new int[arr.length];
        for(int i=0;i<arr.length;++i){
            Integer lower = ts.lower(arr[i]);
            res[i] = lower==null ? -1 : lower;
            ts.add(arr[i]);
        }
        return res;
    }
```

### Time Complexity: O(n* logn)
### Space Complexity: O(n+n)