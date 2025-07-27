# Question

Given two sorted arrays a[] and b[], where each array may contain duplicate elements , the task is to return the elements in the union of the two arrays in sorted order.

Union of two arrays can be defined as the set containing distinct common elements that are present in either of the arrays.

##### Examples:

Input: a[] = [1, 2, 3, 4, 5], b[] = [1, 2, 3, 6, 7]

Output: 1 2 3 4 5 6 7

Explanation: Distinct elements including both the arrays are: 1 2 3 4 5 6 7.


### Solve: [https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1)

***

# BruteForce Solution

``` java
public static ArrayList<Integer> findUnion(int a[], int b[]) {
    TreeSet<Integer> ts = new TreeSet<>();
    for(int i: a) ts.add(i);
    for(int i: b) ts.add(i);
    return new ArrayList<>(ts);
}
```

### Time Complexity: O(n1*logn1)+O(n2*logn2)
### Space Complexity: O(n1+n2)+O(n1+n2)


# Optimal Solution

``` java
public static ArrayList<Integer> findUnion(int a[], int b[]) {
    ArrayList<Integer> ls = new ArrayList<>();
    int pnt1 = 0, pnt2 = 0;
    int n1 = a.length, n2 = b.length;
    
    if(a[pnt1]<b[pnt2]) ls.add(a[pnt1++]);
    else ls.add(b[pnt2++]);
    
    while(pnt1<n1 && pnt2<n2){
        if(a[pnt1]<b[pnt2]){
            if(a[pnt1]!=ls.get(ls.size()-1))
                ls.add(a[pnt1]);
            pnt1++;
        }
        else{
            if(b[pnt2]!=ls.get(ls.size()-1))
                ls.add(b[pnt2]);
            pnt2++;
        }
    }
    while(pnt1<n1){
        if(a[pnt1]!=ls.get(ls.size()-1))
            ls.add(a[pnt1]);
        pnt1++;
    }
    while(pnt2<n2){
        if(b[pnt2]!=ls.get(ls.size()-1))
            ls.add(b[pnt2]);
        pnt2++;
    }
    return ls;
}
```

### Time Complexity: O(n1+n2)
### Space Complexity: O(n1+n2)