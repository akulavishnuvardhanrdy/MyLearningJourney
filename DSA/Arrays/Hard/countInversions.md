# Question

Given an array of integers arr[]. You have to find the Inversion Count of the array. 
Note : Inversion count is the number of pairs of elements (i, j) such that i < j and arr[i] > arr[j].

 

##### Example:

Input: arr[] = [2, 4, 1, 3, 5]

Output: 3

Explanation: The sequence 2, 4, 1, 3, 5 has three inversions (2, 1), (4, 1), (4, 3).

### Solve: [https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1](https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1)

***

# Optimal Solution


``` java
    int count =0;
    int inversionCount(int arr[]) {
        // Code Here
        mergeSort(arr,0,arr.length-1);
        return count;
    }
    
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
            else{
                count+=(mid-i+1);
                b[pnt++] = arr[j++];}
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

### Time Complexity: O(n*logn)
### Space Complexity: O(n)