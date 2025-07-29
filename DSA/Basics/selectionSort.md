# Question

Given an array arr, use selection sort to sort arr[] in increasing order.
 

##### Example 1:

Input: arr[] = [4, 1, 3, 9, 7]

Output: [1, 3, 4, 7, 9]

Explanation: Maintain sorted (in bold) and unsorted subarrays. Select 1. Array becomes 1 4 3 9 7. Select 3. Array becomes 1 3 4 9 7. Select 4. Array becomes 1 3 4 9 7. Select 7. Array becomes 1 3 4 7 9. Select 9. Array becomes 1 3 4 7 9.

### Solve: [https://www.geeksforgeeks.org/problems/selection-sort/1](https://www.geeksforgeeks.org/problems/selection-sort/1)

***

# Optimal Solution

``` java
    void selectionSort(int[] arr) {
        // code here
        int n = arr.length;
        for(int i=0;i<n;++i){
            int min = arr[i];
            int minIdx = i;
            for(int j=i;j<n;++j){
                if(arr[j]<min){
                    min = arr[j];
                    minIdx = j;
                }
            }
            int temp = arr[minIdx];
            arr[minIdx] = arr[i];
            arr[i] = temp;
        }
    }
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)
