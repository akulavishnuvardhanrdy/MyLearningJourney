# Question

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
 

##### Example:

Input: prices = [7,1,5,3,6,4]

Output: 5

Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

### Solve: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

***

# Optimal Solution


``` java
    public int maxProfit(int[] prices) {
        int profit = 0;
        int min = prices[0];
        for(int i: prices){
            int currProfit = i-min;
            if(currProfit>profit)
                profit = currProfit;
            if(min>i)
                min = i;
        }
        return profit;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)