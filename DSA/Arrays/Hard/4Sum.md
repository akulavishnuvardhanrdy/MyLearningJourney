# Question

Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
You may return the answer in any order.

 
 

##### Example:

Input: nums = [1,0,-1,0,-2,2], target = 0

Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

### Solve: [https://leetcode.com/problems/4sum/description/](https://leetcode.com/problems/4sum/description/)

***

# Optimal Solution


``` java
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        int n = nums.length;
        for(int i=0;i<n;++i){
            if(i!=0 && nums[i]==nums[i-1])
                continue;
            for(int j=i+1;j<n;++j){
                if(j!=i+1 && nums[j]==nums[j-1])
                    continue;
                int pnt1=j+1,pnt2=n-1;
                while(pnt1<pnt2){
                    long sum = (long)nums[i]+nums[j]+nums[pnt1]+nums[pnt2];
                    if(sum==target){
                        List<Integer> ls = new ArrayList<>(Arrays.asList(nums[i],nums[j],nums[pnt1],nums[pnt2]));
                    if(res.size()==0 || !ls.equals(res.get(res.size()-1)))
                        res.add(ls);
                    }
                    if(sum<target)
                        pnt1++;
                    else
                        pnt2--;
                }
            }
        }
        return res;
    }
```

### Time Complexity: O(n^3)+O(n*logn)
### Space Complexity: O(no of quads)