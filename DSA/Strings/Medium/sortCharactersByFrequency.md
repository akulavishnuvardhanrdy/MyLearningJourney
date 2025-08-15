# Question

Given a string s, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string.

Return the sorted string. If there are multiple answers, return any of them.



##### Example:

Input: s = "tree"

Output: "eert"

Explanation: 'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.



### Solve: [https://leetcode.com/problems/sort-characters-by-frequency/](https://leetcode.com/problems/sort-characters-by-frequency/)

***

# Optimal Solution
        

``` java
    public String frequencySort(String s) {
        int count[] = new int[123];
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b)->b.count-a.count);
        StringBuilder str = new StringBuilder();
        for(int i=0;i<s.length();++i){
            count[s.charAt(i)]++;
        }
        for(int i=0;i<123;++i){
            if(count[i]!=0)
                pq.add(new Pair((char)i,count[i]));
        }
        while(!pq.isEmpty()){
            Pair p = pq.poll();
            while(p.count>0){
                str.append(p.ch);
                p.count--;
            }
        }
        return str.toString();
    }
```

### Time Complexity: O(n*logK)
### Space Complexity: O(k+123)