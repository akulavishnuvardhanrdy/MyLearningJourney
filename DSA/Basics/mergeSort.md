# Question

Given an array arr[], its starting position l and its ending position r. Sort the array using the merge sort algorithm.

##### Example 1:

Input: arr[] = [4, 1, 3, 9, 7]

Output: [1, 3, 4, 7, 9]

Explanation: We get the sorted array after using merge sort

### Solve: [https://www.geeksforgeeks.org/problems/merge-sort/1](https://www.geeksforgeeks.org/problems/merge-sort/1)

***

# Optimal Solution

``` java
    void mergeSort(int arr[], int l, int r) {
        // code here
        if(l<r){
            int mid = (r+l)/2;
            mergeSort(arr,l,mid);
            mergeSort(arr,mid+1,r);
            merge(arr,l,mid,r);
        }
    }
    
    void merge(int arr[], int l, int mid,int r){
        int i=l,j=mid+1;
        int b[] = new int[r-l+1];
        int pnt =0;
        while(i<=mid && j<=r){
            if(arr[i]<=arr[j])
                b[pnt++] = arr[i++];
            else
                b[pnt++] = arr[j++];
        }
        while(i<=mid)
            b[pnt++] = arr[i++];
        while(j<=r)
            b[pnt++] = arr[j++];
        for(int k=0;k<b.length;++k){
            arr[k+l] = b[k];
        }
    }
```

### Time Complexity: O(n*logN)
### Space Complexity: O(n)
