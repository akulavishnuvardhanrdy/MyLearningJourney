# Question

Given an array arr[] of positive integers.The task is to complete the insertsort() function which is used to implement Insertion Sort.
 

##### Example 1:

Input: arr[] = [4, 1, 3, 9, 7]

Output: [1, 3, 4, 7, 9]

Explanation: The sorted array will be [1, 3, 4, 7, 9].

### Solve: [https://www.geeksforgeeks.org/problems/insertion-sort/1](https://www.geeksforgeeks.org/problems/insertion-sort/1)

***

# Optimal Solution

``` java
    public void insertionSort(int arr[]) {
        // code here
        int n=arr.length;
        for(int i=1;i<n;++i){
            for(int j=i;j>0;--j){
                if(arr[j-1]>arr[j])
                    swap(arr,j,j-1);
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
