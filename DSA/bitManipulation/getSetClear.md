**Question**:  
Given a 32 bit unsigned integer num and an integer i. Perform following operations on the number -   
1. Get ith bit  
2. Set ith bit  
3. Clear ith bit    

**Solutions**:   


**Optimal Solution**:  

    static void bitManipulation(int num, int i) {
        int mask = 1<<(i-1);
        int temp = (num&mask)==0 ?0:1;
        int set = temp==1 ? num : num|mask;
        int clear = temp==0 ? num : num& ~mask;
        System.out.print(temp+" "+set+" "+clear);
    }

Time Complexity: O(1)  
Space Complexity: O(1) 