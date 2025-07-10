**Question**:  
You are given two numbers a and b. Your task is to swap the given two numbers.    

**Solutions**:   


**Optimal Solution**:  

    static List<Integer> get(int a, int b) {
        List<Integer> ls = new ArrayList<>();
        a=a^b;
        b=a^b;
        a=a^b;
        ls.add(a);
        ls.add(b);
        return ls;
    }

Time Complexity: O(1)  
Space Complexity: O(1)