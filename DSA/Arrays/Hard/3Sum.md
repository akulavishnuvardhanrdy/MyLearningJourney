# Question

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

 
 

##### Example:

Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]

Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

### Solve: [https://leetcode.com/problems/3sum/description/](https://leetcode.com/problems/3sum/description/)

***

# Optimal Solution


``` java
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        int n = nums.length;
        for(int i=0;i<n;++i){
            if(i!=0 && nums[i]==nums[i-1])
                continue;
            int pnt1 = i+1, pnt2 = n-1;
            while(pnt1<pnt2){
                if(nums[pnt1]+nums[pnt2]==-(nums[i])){
                    List<Integer> ls = new ArrayList<>(Arrays.asList(nums[i],nums[pnt1],nums[pnt2]));
                    if(res.size()==0 || !res.get(res.size()-1).equals(ls))
                        res.add(ls);
                }
                if(nums[pnt1]+nums[pnt2]>-(nums[i]))
                    pnt2--;
                else
                    pnt1++;
            }
        }
        return res;
    }
```

### Time Complexity: O(n^2)+O(n*logn)
### Space Complexity: O(no of triplets)