# Question

Given an array of arr[] and Q queries of indices. For each query indices[i], determine the count of elements in arr that are strictly greater than arr[indices[i]] to its right (after the position indices[i]).




##### Example:

Input: arr[] = [3, 4, 2, 7, 5, 8, 10, 6], queries = 2, indices[] = [0, 5]

Output:  [6, 1]

Explanation: The next greater elements to the right of 3(index 0) are 4,7,5,8,10,6. The next greater elements to the right of 8(index 5) is only 10.



### Solve: [https://www.geeksforgeeks.org/problems/number-of-nges-to-the-right/1](https://www.geeksforgeeks.org/problems/number-of-nges-to-the-right/1)
   


# Optimal Solution:  


``` java
    public static int[] count_NGE(int arr[], int indices[]) {
        // code here
        TreeMap<Integer,Integer> map = new TreeMap<>();
        int gre[] = new int[arr.length];
        for(int i=arr.length-1;i>=0;--i){
            NavigableMap<Integer,Integer> greaterMap = map.tailMap(arr[i],false);
            int count = 0;
            for(int freq:greaterMap.values()){
                count +=freq;
            }
            gre[i] = count;
            map.put(arr[i],map.getOrDefault(arr[i],0)+1);
        }
        for(int i=0;i<indices.length;++i){
            int pos = indices[i];
            indices[i] = gre[pos];
        }
        return indices;
    }
```
### Time Complexity: O(n)*O(N*logN)
### Space Complexity: O(N+N)