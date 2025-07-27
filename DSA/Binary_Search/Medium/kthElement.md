# Question  
Given two sorted arrays a[] and b[] and an element k, the task is to find the element that would be at the kth position of the combined sorted array.
 

##### Example 1:

Input: a[] = [2, 3, 6, 7, 9], b[] = [1, 4, 8, 10], k = 5

Output: 6

Explanation: The final combined sorted array would be [1, 2, 3, 4, 6, 7, 8, 9, 10]. The 5th element of this array is 6.

### Solve: [https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1)

***   


# Optimal Solution*  
``` java
    public int kthElement(int nums1[], int nums2[], int k) {
        int n1 = nums1.length,n2 = nums2.length;
        int low = Math.min(nums1[0],nums2[0]);
        int high = Math.max(nums1[n1-1],nums2[n2-1]);
        while(low<=high){
            int count = 0;
            int mid = low+(high-low)/2;
            count+=upperBound(nums1,mid);
            count+=upperBound(nums2,mid);
            if(count<k)
                low = mid+1;
            else
                high = mid-1;
        }
        return low;
    }
    
    int upperBound(int[] arr, int target) {
        int low =0, high = arr.length-1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(arr[mid]<=target)
                low = mid+1;
            else
                high = mid-1;
        }
        return low;
    }
```
### Time Complexity: O(log(max-min)*(logN+logM))  
### Space Complexity: O(1)  