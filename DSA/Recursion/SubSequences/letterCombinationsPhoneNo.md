# Question  

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.





##### Examples :

Input: digits = "23"

Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]



### Solve: [https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

*** 

# Optimal Solution 

``` java
    public List<String> letterCombinations(String digits) {
        List<String> res = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        if(digits.length()==0)
            return res;
        Map<Character,String> map = new HashMap<>();
        map.put('2',"abc");
        map.put('3',"def");
        map.put('4',"ghi");
        map.put('5',"jkl");
        map.put('6',"mno");
        map.put('7',"pqrs");
        map.put('8',"tuv");
        map.put('9',"wxyz");
        findCombinations(map,digits,res,sb,0);
        return res;
    }
    void findCombinations(Map<Character,String> map,String digits,List<String> res,StringBuilder sb,int idx){
        if(idx==digits.length()){
            res.add(sb.toString());
            return ;
        }
        char digit = digits.charAt(idx);
        String com = map.get(digit);
        for(int i=0;i<com.length();++i){
            sb.append(com.charAt(i));
            findCombinations(map,digits,res,sb,idx+1);
            sb.setLength(sb.length()-1);
        }
    }
```