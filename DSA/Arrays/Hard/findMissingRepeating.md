# Question

Given an unsorted array arr[] of size n, containing elements from the range 1 to n, it is known that one number in this range is missing, and another number occurs twice in the array, find both the duplicate number and the missing number.

 

##### Example:

Input: arr[] = [2, 2]

Output: [2, 1]

Explanation: Repeating number is 2 and the missing number is 1.

### Solve: [https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1)

***

# Optimal Solution


``` java
    ArrayList<Integer> findTwoElement(int arr[]) {
        boolean temp[] = new boolean[arr.length];
        int n = arr.length;
        ArrayList<Integer> ls = new ArrayList<>();
        for(int i=0;i<n;++i){
            if(temp[arr[i]-1])
                ls.add(arr[i]);
            temp[arr[i]-1] = true;
        }
        for(int i=0;i<n;++i){
            if(!temp[i]){
                ls.add(i+1);
                break;
            }
        }
        return ls;
    }
```

### Time Complexity: O(2n)
### Space Complexity: O(n)