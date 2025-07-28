# Question

A permutation of an array of integers is an arrangement of its members into a sequence or linear order.

For example, for arr = [1,2,3], the following are all the permutations of arr: [1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].
The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

For example, the next permutation of arr = [1,2,3] is [1,3,2].
Similarly, the next permutation of arr = [2,3,1] is [3,1,2].
While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.
Given an array of integers nums, find the next permutation of nums.

The replacement must be in place and use only constant extra memory.
 

##### Example:

Input: nums = [1,2,3]

Output: [1,3,2]

### Solve: [https://leetcode.com/problems/next-permutation/description/](https://leetcode.com/problems/next-permutation/description/)

***

# Optimal Solution


``` java
    public void nextPermutation(int[] nums) {
        int pivot = findPivot(nums);
        int successor;
        if(pivot==-1) successor = nums.length-1;
        else successor = findSuccessor(nums,pivot);
        if(pivot!=-1){
            swap(nums,pivot,successor);
        }
        pivot++;
        reverse(nums,pivot,nums.length-1);
    }

    int findPivot(int nums[]){
        int j= nums.length-2;
        while(j>=0){
            if(nums[j]<nums[j+1])
                return j;
            j--;
        }
        return -1;
    }

    public void reverse(int[] nums, int pivot, int successor){
        while(pivot<successor){
            int temp = nums[pivot];
            nums[pivot] = nums[successor];
            nums[successor] = temp;
            pivot++;
            successor--;
        }
    }

    public void swap(int[] nums,int i,int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    int findSuccessor(int nums[],int pivot){
        int j = nums.length-1;
        while(j>=pivot){
            if(nums[j]>nums[pivot])
                return j;
            j--;
        }
        return nums.length-1;
    }
```

### Time Complexity: O(3n)
### Space Complexity: O(1)