# Question

Given an unsorted array, arr[] of positive numbers that contains even number of occurrences for all numbers except two numbers. Return that two numbers in decreasing order which has odd occurrences.




##### Example:

Input: arr = [4, 2, 4, 5, 2, 3, 3, 1]

Output: [5, 1] 

Explanation: 5 and 1 have odd occurrences.


### Solve: [https://www.geeksforgeeks.org/problems/two-numbers-with-odd-occurrences5846/1](https://www.geeksforgeeks.org/problems/two-numbers-with-odd-occurrences5846/1)
   


# Optimal Solution:  
``` java
    ArrayList<Integer> twoOddNum(int[] arr) {
        // code here
        int xor = 0;
        for(int i:arr)
            xor^=i;
        int pos = Integer.numberOfTrailingZeros(xor&-xor);
        int xor1=0,xor2=0;
        for(int i:arr){
            int bit = (i>>pos)&1;
            if(bit==0)
                xor1^=i;
            else
                xor2^=i;
        }
        ArrayList<Integer> res = new ArrayList<>();
        res.add(xor1);
        if(xor1>=xor2)
            res.add(xor2);
        else
            res.add(0,xor2);
        return res;
    }
```
### Time Complexity: O(2N)
### Space Complexity: O(2) 