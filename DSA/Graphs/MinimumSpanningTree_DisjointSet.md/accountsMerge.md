# Question  

Given a list of accounts where each element accounts[i] is a list of strings, where the first element accounts[i][0] is a name, and the rest of the elements are emails representing emails of the account.

Now, we would like to merge these accounts. Two accounts definitely belong to the same person if there is some common email to both accounts. Note that even if two accounts have the same name, they may belong to different people as people could have the same name. A person can have any number of accounts initially, but all of their accounts definitely have the same name.

After merging the accounts, return the accounts in the following format: the first element of each account is the name, and the rest of the elements are emails in sorted order. The accounts themselves can be returned in any order.



##### Examples :

Input: accounts = [["John","johnsmith@mail.com","john_newyork@mail.com"],["John","johnsmith@mail.com","john00@mail.com"],["Mary","mary@mail.com"],["John","johnnybravo@mail.com"]]

Output: [["John","john00@mail.com","john_newyork@mail.com","johnsmith@mail.com"],["Mary","mary@mail.com"],["John","johnnybravo@mail.com"]]

Explanation:
The first and second John's are the same person as they have the common email "johnsmith@mail.com".
The third John and Mary are different people as none of their email addresses are used by other accounts.
We could return these lists in any order, for example the answer [['Mary', 'mary@mail.com'], ['John', 'johnnybravo@mail.com'], 
['John', 'john00@mail.com', 'john_newyork@mail.com', 'johnsmith@mail.com']] would still be accepted.




### Solve: [https://leetcode.com/problems/accounts-merge/](https://leetcode.com/problems/accounts-merge/)

*** 

# Optimal Solution 

``` java
class Solution {
    public List<List<String>> accountsMerge(List<List<String>> accounts) {
        int n = accounts.size();
        Map<String,Integer> map = new HashMap<>();
        UnionFind dsu = new UnionFind(n);
        for(int i=0;i<n;++i){
            for(int j=1;j<accounts.get(i).size();++j){
                String str = accounts.get(i).get(j);
                if(!map.containsKey(str)){
                    map.put(str,i);
                }
                else{
                    dsu.union(i,map.get(str));
                }
            }
        }
        List<List<String>> temp = new ArrayList<>();
        for(int i=0;i<n;++i)
            temp.add(new ArrayList<>());
        for(Map.Entry<String,Integer> entry:map.entrySet()){
            int p = dsu.find(entry.getValue());
            temp.get(p).add(entry.getKey());
        }
        List<List<String>> res = new ArrayList<>();
        for(int i=0;i<temp.size();++i){
            if(temp.get(i).size()==0)
                continue;
            Collections.sort(temp.get(i));
            List<String> dummy = new ArrayList<>();
            dummy.add(accounts.get(i).get(0));
            for(String email:temp.get(i))
                dummy.add(email);
            res.add(dummy);
        }
        return res;
    }
}
class UnionFind{
    int par[],rank[];
    UnionFind(int n){
        par = new int[n];
        rank = new int[n];
        for(int i=0;i<n;++i){
            par[i] = i;
            rank[i] = 1;
        }
    }
    int find(int n){
        if(par[n]==n)
            return n;
        return par[n] = find(par[n]);
    }
    void union(int u,int v){
        int pu = find(u);
        int pv = find(v);
        if(pu==pv)
            return ;
        if(rank[pu]<rank[pv])
            par[pu] = pv;
        else if(rank[pu]>rank[pv])
            par[pv] = pu;
        else{
            par[pv] = pu;
            rank[pu]++;
        }
    }
}
```