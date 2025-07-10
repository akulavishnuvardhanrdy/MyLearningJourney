**Question**:  
Given two positive integer n and  k, check if the kth index bit of n is set or not.  
 Note: A bit is called set if it is 1.    

**Solutions**:   


**Optimal Solution**:  

    static boolean checkKthBit(int n, int k) {
        int mask = 1<<k;
        boolean temp = (n&mask) ==0?false:true;
        return temp;
    }

Time Complexity: O(1)  
Space Complexity: O(1) 