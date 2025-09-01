# Question

Given two arrays, val[] and wt[], representing the values and weights of items, and an integer capacity representing the maximum weight a knapsack can hold, determine the maximum total value that can be achieved by putting items in the knapsack. You are allowed to break items into fractions if necessary.
Return the maximum value as a double, rounded to 6 decimal places.


##### Example:

Input: val[] = [60, 100, 120], wt[] = [10, 20, 30], capacity = 50

Output: 240.000000

Explanation: Take the item with value 60 and weight 10, value 100 and weight 20 and split the third item with value 120 and weight 30, to fit it into weight 20. so it becomes (120/30)*20=80, so the total value becomes 60+100+80.0=240.0 Thus, total maximum value of item we can have is 240.00 from the given capacity of sack. 


### Solve: [https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)

***

# Optimal Solution
        

``` java
class Solution {
    double fractionalKnapsack(int[] values, int[] weights, int W) {
        // code here
        double res = 0;
        Pair[] temp = new Pair[values.length];
        for(int i=0;i<values.length;++i){
            temp[i] = new Pair((double)values[i]/weights[i],i);
        }
        Arrays.sort(temp,(a,b)->Double.compare(b.value,a.value));
        int pos = 0;
        while(W>0 && pos<temp.length){
            int index = temp[pos].index;
            if(weights[index]<=W){
                res+=values[index];
                W-=weights[index];
            }
            else{
                res+=(((double)values[index]/weights[index])*W);
                W=0;
            }
            pos++;
        }
        return Math.round(res*1_000_000.0)/1_000_000.0;
    }
}

class Pair{
    double value;
    int index;
    public Pair(double value, int index){
        this.value = value;
        this.index = index;
    }
}
```

### Time Complexity: O(nlogn)
### Space Complexity: O(n)