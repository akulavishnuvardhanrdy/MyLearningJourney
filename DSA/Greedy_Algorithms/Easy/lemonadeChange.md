# Question

At a lemonade stand, each lemonade costs $5. Customers are standing in a queue to buy from you and order one at a time (in the order specified by bills). Each customer will only buy one lemonade and pay with either a $5, $10, or $20 bill. You must provide the correct change to each customer so that the net transaction is that the customer pays $5.

Note that you do not have any change in hand at first.

Given an integer array bills where bills[i] is the bill the ith customer pays, return true if you can provide every customer with the correct change, or false otherwise.



##### Example:

Input: bills = [5,5,5,10,20]

Output: true

Explanation: 
From the first 3 customers, we collect three $5 bills in order.
From the fourth customer, we collect a $10 bill and give back a $5.
From the fifth customer, we give a $10 bill and a $5 bill.
Since all customers got correct change, we output true. 



### Solve: [https://leetcode.com/problems/lemonade-change/](https://leetcode.com/problems/lemonade-change/)

***

# Optimal Solution
        

``` java
    public boolean lemonadeChange(int[] bills) {
        int count5 = 0;
        int count10 = 0;
        for(int i=0;i<bills.length;++i){
            int bill = bills[i];
            if(bill==5)
                count5++;
            else if(bill==10)
                count10++;
            bill-=5;
            if(bill>=10 && count10>0){
                count10--;
                bill-=10;
            }
            while(bill>=5 && count5>0){
                count5--;
                bill-=5;
            }
            if(bill>0)
                return false;
        }
        return true;
    }
```

### Time Complexity: O(n)
### Space Complexity: O(1)