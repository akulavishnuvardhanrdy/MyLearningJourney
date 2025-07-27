# Question

Given an array of positive integers arr[], return the second largest element from the array. If the second largest element doesn't exist then return -1.

Note: The second largest element should not be equal to the largest element.

##### Examples:

Input: arr[] = [12, 35, 1, 10, 34, 1]

Output: 34

Explanation: The largest element of the array is 35 and the second largest element is 34.

### Solve: [https://www.geeksforgeeks.org/problems/second-largest3735/1](https://www.geeksforgeeks.org/problems/second-largest3735/1)

***

# Brute Force Solution

``` java
    public int getSecondLargest(int[] arr) {
        int max = -1;
        int sec = -1;
        for(int i:arr){
            if(i>max){
                sec = max;
                max =i;
            }
            if(i>sec && i!=max) sec = i;
        }
        return sec;
    }
```

### Time Complexity: O(n*logn)+O(n)
### Space Complexity: O(1)


# Better Solution Solution

``` java
public int getSecondLargest(int[] arr) {
    int max=arr[0];
    for(int i=0;i<arr.length;++i){
        if(arr[i]>max) max = arr[i];
    }
    int sec=-1;
    for(int i=0;i<arr.length;++i){
        if(arr[i]>sec && arr[i]!=max){
            sec = arr[i];
        }
    }
    return sec;
}
```

### Time Complexity: O(N)+O(n)
### Space Complexity: O(1)



# Optimal Solution

``` java
public int getSecondLargest(int[] arr) {
    return findSecond(arr,-1,arr[0],0);
}

int findSecond(int arr[], int sec, int max, int i){
    if(i==arr.length) return sec;
    if(arr[i]>max){
        sec=max;
        max=arr[i];
    }
    if(arr[i]>sec && arr[i]!=max){
        sec=arr[i];
    }
    return findSecond(arr,sec,max,i+1);
}
```

### Time Complexity: O(n)
### Space Complexity: O(1)