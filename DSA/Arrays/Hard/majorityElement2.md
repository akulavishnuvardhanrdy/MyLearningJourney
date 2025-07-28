# Question

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.
 

##### Example:

Input: nums = [3,2,3]

Output: [3]

### Solve: [https://leetcode.com/problems/majority-element-ii/](https://leetcode.com/problems/majority-element-ii/)

***

# Optimal Solution


``` java
    public List<Integer> majorityElement(int[] nums) {
        int n = nums.length;
        List<Integer> res = new ArrayList<>();
        int ele1 = -1, ele2 = -1;
        int count1=0,count2=-0;
        for(int i:nums){
            if(ele1!=-1 && ele1==i)
                count1++;
            else if(ele2!=-1 && ele2==i)
                count2++;
            else if(count1==0){
                ele1 = i;
                count1=1;
            }
            else if(count2==0){
                ele2 = i;
                count2 = 1;
            }
            else{
                count1--;
                count2--;
            }
        }
        count1=0;
        count2=0;
        for(int i : nums){
            if(i==ele1) count1++;
            if(i==ele2) count2++;
        }
        if(count1>n/3) res.add(ele1);
        if(ele1==ele2) return res;
        if(count2>n/3) res.add(ele2);
        return res;
    }
```

### Time Complexity: O(2n)
### Space Complexity: O(2)