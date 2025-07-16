**Question**:  
Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer.    

**Solutions**:   


**Optimal Solution**:  

    public int myAtoi(String s) {
        int i=0,sign =1, res = 0;
        s = s.trim();
        int n = s.length();
        if(s==null || s.isEmpty())
            return 0;
        if(s.charAt(0)=='-' || s.charAt(0)=='+'){
            i++;
            sign = s.charAt(0)=='-' ? -1:1;
        }
        while(i<n && Character.isDigit(s.charAt(i))){
            int digit = s.charAt(i)-'0';
            if(res>(Integer.MAX_VALUE-digit)/10){
                return sign==1?Integer.MAX_VALUE:Integer.MIN_VALUE;
            }
            res = res*10+digit;
            i++;
        }
        return res*sign;
    }

Time Complexity: O(N)  
Space Complexity: O(1)