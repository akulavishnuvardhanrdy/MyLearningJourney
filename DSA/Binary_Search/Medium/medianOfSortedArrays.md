# Question  
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).
 

##### Example 1:

Input: nums1 = [1,3], nums2 = [2]

Output: 2.00000

Explanation: merged array = [1,2,3] and median is 2.

### Solve: [https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)

***   


# Optimal Solution*  
``` java
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n1 = nums1.length,n2 = nums2.length;
        if (n1 == 0) return findMedianSingle(nums2);
        if (n2 == 0) return findMedianSingle(nums1);
        int len = n1+n2;
        int medIdx = (n1+n2)/2+1;
        if(len%2!=0)
            return (double)func(nums1,nums2,medIdx);
        else
            return ((double)func(nums1,nums2,medIdx)+func(nums1,nums2,medIdx-1))/2;
        
    }

    public int func(int nums1[],int nums2[],int medIdx){
        int n1 = nums1.length,n2 = nums2.length;
        int low = Math.min(nums1[0],nums2[0]);
        int high = Math.max(nums1[n1-1],nums2[n2-1]);
        while(low<=high){
            int count = 0;
            int mid = low+(high-low)/2;
            count+=upperBound(nums1,mid);
            count+=upperBound(nums2,mid);
            if(count<medIdx)
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

    double findMedianSingle(int[] arr) {
        int n = arr.length;
        if (n % 2 == 1) return arr[n / 2];
        return (arr[n / 2 - 1] + arr[n / 2]) / 2.0;
    }
```
### Time Complexity: O(log(max-min)*(logn+logm))  
### Space Complexity: O(1)  