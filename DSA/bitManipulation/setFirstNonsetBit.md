**Question**:  
Given a non-negative number n . The problem is to set the rightmost unset bit in the binary representation of n.    

**Solutions**:   


**Optimal Solution**:  

    static int setBit(int n) {
        return n|n+1;
    }

Time Complexity: O(1)  
Space Complexity: O(1)