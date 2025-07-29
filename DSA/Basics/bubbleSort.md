# Question

Given an array, arr[]. Sort the array using bubble sort algorithm.
 

##### Example 1:

Input: arr[] = [4, 1, 3, 9, 7]

Output: [1, 3, 4, 7, 9]

Explanation: After Sorting the array in ascending order of their values is [1, 3, 4, 7, 9].

### Solve: [https://www.geeksforgeeks.org/problems/bubble-sort/1](https://www.geeksforgeeks.org/problems/bubble-sort/1)

***

# Optimal Solution

``` java
    public void bubbleSort(int[] arr) {
        // code here
        int n= arr.length;
        for(int i=n-1;i>=0;--i){
            for(int j=0;j<i;++j){
                if(arr[j]>arr[j+1])
                    swap(arr,j,j+1);
            }
        }
    }
    
    void swap(int arr[],int i,int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
```

### Time Complexity: O(n^2)
### Space Complexity: O(1)
