# Question

Given a sorted doubly linked list of positive distinct elements, the task is to find pairs in a doubly-linked list whose sum is equal to given value target.



##### Example:

Input:  
1 <-> 2 <-> 4 <-> 5 <-> 6 <-> 8 <-> 9
target = 7

Output: (1, 6), (2,5)

Explanation: We can see that there are two pairs 
(1, 6) and (2,5) with sum 7.


### Solve: [https://www.geeksforgeeks.org/problems/find-pairs-with-given-sum-in-doubly-linked-list/1](https://www.geeksforgeeks.org/problems/find-pairs-with-given-sum-in-doubly-linked-list/1)
   


# Optimal Solution:  


``` java
    public static ArrayList<ArrayList<Integer>> findPairsWithGivenSum(int target,
                                                                      Node head) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        Node first = head;
        Node last = head;
        while(last.next!=null)
            last = last.next;
        while(first!=last && last.next!=first){
            int sum = first.data+last.data;
            if(sum==target){
                ArrayList<Integer> temp = new ArrayList<>();
                temp.add(first.data);
                temp.add(last.data);
                res.add(temp);
                first = first.next;
                last = last.prev;
            }
            else if(sum>target)
                last = last.prev;
            else 
                first = first.next;
        }
        return res;
    }
```
### Time Complexity: O(N)+O(N/2)
### Space Complexity: O(1)