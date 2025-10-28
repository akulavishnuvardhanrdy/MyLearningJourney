# Question  

A transformation sequence from word beginWord to word endWord using a dictionary wordList is a sequence of words beginWord -> s1 -> s2 -> ... -> sk such that:

Every adjacent pair of words differs by a single letter.
Every si for 1 <= i <= k is in wordList. Note that beginWord does not need to be in wordList.
sk == endWord
Given two words, beginWord and endWord, and a dictionary wordList, return the number of words in the shortest transformation sequence from beginWord to endWord, or 0 if no such sequence exists.



##### Examples :

Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]

Output: 5

Explanation: One shortest transformation sequence is "hit" -> "hot" -> "dot" -> "dog" -> cog", which is 5 words long.




### Solve: [https://leetcode.com/problems/word-ladder/](https://leetcode.com/problems/word-ladder/)

*** 

# Optimal Solution 

``` java
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> set = new HashSet<>();
        ArrayDeque<Pair> q = new ArrayDeque<>();
        for(String s:wordList){
            set.add(s);
        }
        if(!set.contains(endWord))
            return 0;
        q.addLast(new Pair(beginWord,1));
        while(!q.isEmpty()){
            Pair node = q.pollFirst();
            for(int i=0;i<node.str.length();++i){
                char ori = node.str.charAt(i);
                for(int j=0;j<26;++j){
                    char ch = (char)(j+'a');
                    if(ch==ori)
                        continue;
                    String temp = node.str.substring(0,i)+ch+node.str.substring(i+1);
                    if(temp.equals(endWord)){
                        return node.dis+1;
                    }
                    if(set.contains(temp)){
                        q.addLast(new Pair(temp,node.dis+1));
                        set.remove(temp);
                    }
                }
            }
        }
        return 0;
    }
    static class Pair{
        String str;
        int dis;
        public Pair(String str,int dis){
            this.str = str;
            this.dis = dis;
        }
    }
```