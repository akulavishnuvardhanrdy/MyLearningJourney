# Question

Given an integer array nums, return the number of reverse pairs in the array.

A reverse pair is a pair (i, j) where:

0 <= i < j < nums.length and
nums[i] > 2 * nums[j].
 

##### Example:

Input: nums = [1,3,2,3,1]

Output: 2

Explanation: The reverse pairs are:
(1, 4) --> nums[1] = 3, nums[4] = 1, 3 > 2 * 1
(3, 4) --> nums[3] = 3, nums[4] = 1, 3 > 2 * 1

### Solve: [https://leetcode.com/problems/reverse-pairs/description/](https://leetcode.com/problems/reverse-pairs/description/)

***

# Optimal Solution


``` java
    int count = 0;
    public int reversePairs(int[] nums) {
        mergeSort(nums,0,nums.length-1);
        return count;
    }

    void mergeSort(int arr[], int l, int r) {
        if(l<r){
            int mid = (r+l)/2;
            mergeSort(arr,l,mid);
            mergeSort(arr,mid+1,r);
            countReversePairs(arr,l,mid,r);
            merge(arr,l,mid,r);
        }
    }

    void countReversePairs(int arr[],int l,int mid,int r){
        int i=l,j=mid+1;
        while(i<=mid && j<=r){
            if((long)arr[i]>(long)2*arr[j]){
                count+=(mid-i+1);
                j++;
            }
            else
                i++;
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
                b[pnt++] = arr[j++];
            }
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

### Time Complexity: O(n*logn+ n*logn)
### Space Complexity: O(n)