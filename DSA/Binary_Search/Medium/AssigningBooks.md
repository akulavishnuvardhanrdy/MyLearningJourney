# Question  
Given an array arr[] of integers, where each element arr[i] represents the number of pages in the i-th book. You also have an integer k representing the number of students. The task is to allocate books to each student such that:

Each student receives atleast one book.
Each student is assigned a contiguous sequence of books.
No book is assigned to more than one student.

The objective is to minimize the maximum number of pages assigned to any student. In other words, out of all possible allocations, find the arrangement where the student who receives the most pages still has the smallest possible maximum.
 

##### Example 1:

Input: arr[] = [12, 34, 67, 90], k = 2

Output: 113

Explanation: Allocation can be done in following ways:
             => [12] and [34, 67, 90] Maximum Pages = 191
             => [12, 34] and [67, 90] Maximum Pages = 157
             => [12, 34, 67] and [90] Maximum Pages = 113.
             Therefore, the minimum of these cases is 113, which is selected as the output.

### Solve: [https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

***   


# Optimal Solution*  
``` java
    public static int findPages(int[] arr, int k) {
        // code here
        if(arr.length<k){
            return -1;
        }
        int temp[] = MaxTotal(arr);
        int low = temp[0], high = temp[1];
        int res = -1;
        while(low<=high){
            int mid = low+(high-low)/2;
            if(!isPossible(arr,k,mid)){
                low = mid+1;
            }
            else{
                high =mid-1;
                res = mid;
            }
        }
        return res;
    }
    
    static boolean isPossible(int arr[], int k, int maxPages){
        int students = 1;
        int currSum = 0;
        for(int i:arr){
            if(currSum+i>maxPages){
                students++;
                currSum = i;
                if(students>k) return false;
            }
            else{
                currSum+=i;
            }
        }
        return true;
    }
    
    static int[] MaxTotal(int arr[]){
        int sum =0,max=Integer.MIN_VALUE;
        for(int i:arr){
            sum+=i;
            if(i>max) max = i;
        }
        return new int[]{max,sum};
    }
```
### Time Complexity: O(N*log(sumElements - maxElement))  
### Space Complexity: O(1) 