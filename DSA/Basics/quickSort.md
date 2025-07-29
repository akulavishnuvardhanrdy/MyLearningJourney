# Question

Implement Quick Sort, a Divide and Conquer algorithm, to sort an array, arr[] in ascending order.
Given an array arr[], with starting index low and ending index high, complete the functions partition() and quickSort().
Use the last element as the pivot, so that all elements less than or equal to the pivot come before it, and elements greater than the pivot follow it.
 

##### Example 1:

Input: arr[] = [4, 1, 3, 9, 7]

Output: [1, 3, 4, 7, 9]

Explanation: After sorting, all elements are arranged in ascending order.

### Solve: [https://www.geeksforgeeks.org/problems/quick-sort/1](https://www.geeksforgeeks.org/problems/quick-sort/1)

***

# Optimal Solution

``` java
    public void quickSort(int[] arr, int low, int high) {
        // code here
        if(low<high){
            int mid = partition(arr,low,high);
            quickSort(arr,low,mid-1);
            quickSort(arr,mid+1,high);
        }
    }

    private int partition(int[] arr, int low, int high) {
        int i=low,j=low;
        while(j<high){
            if(arr[j]<arr[high]){
                swap(arr,i,j);
                i++;
            }
            j++;
        }
        swap(arr,i,high);
        return i;
    }
    
    void swap(int arr[],int i,int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
```

### Time Complexity: O(n*logn)
### Space Complexity: O(1)
