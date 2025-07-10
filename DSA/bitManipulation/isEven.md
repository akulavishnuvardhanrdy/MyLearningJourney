**Question**:  
Given a positive integer n, determine whether it is odd or even. Return true if the number is even and false if the number is odd.    

**Solutions**:   


**Optimal Solution**:  

    static boolean isEven(int n) {
        return (n&1)==0?true:false;
    }

Time Complexity: O(1)  
Space Complexity: O(1) 