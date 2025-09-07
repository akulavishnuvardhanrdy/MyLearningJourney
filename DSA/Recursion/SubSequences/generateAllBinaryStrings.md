# Question

Given an integer N , Print all binary strings of size N which do not contain consecutive 1s.

A binary string is that string which contains only 0 and 1.




##### Example:

Input:
N = 3

Output:
000 , 001 , 010 , 100 , 101

Explanation:
None of the above strings contain consecutive 1s. "110" is not an answer as it has '1's occuring consecutively. 



### Solve: [https://www.geeksforgeeks.org/problems/generate-all-binary-strings/1](https://www.geeksforgeeks.org/problems/generate-all-binary-strings/1)
   


# Optimal Solution:  
``` java
    public static List<String> generateBinaryStrings(int n) {
        // code here
        List<String> ls = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        generate(ls,sb,n,0,'0');
        return ls;
    }
    public static void generate(List<String> ls,StringBuilder sb,int n,int idx,char last){
        if(idx==n){
            ls.add(sb.toString());
            return;
        }
        sb.append(0);
        generate(ls,sb,n,idx+1,'0');
        sb.setLength(sb.length()-1);
        if(last!='1'){
            sb.append(1);
            generate(ls,sb,n,idx+1,'1');
            sb.setLength(sb.length()-1);
        }
    }
```
### Time Complexity: O(2^n)  
### Space Complexity: O(n) 