# Question

Design a data structure that follows the constraints of a Least Recently Used (LRU) cache.

Implement the LRUCache class:

LRUCache(int capacity) Initialize the LRU cache with positive size capacity.
int get(int key) Return the value of the key if the key exists, otherwise return -1.
void put(int key, int value) Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key.
The functions get and put must each run in O(1) average time complexity.


##### Example:

Input
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]

Output
[null, null, null, 1, null, -1, null, -1, 3, 4]


### Solve: [https://leetcode.com/problems/lru-cache/](https://leetcode.com/problems/lru-cache/)
   


# Optimal Solution:  


``` java
class LRUCache {
    DLL ls;
    int capacity;
    HashMap<Integer,DLL> map;
    DLL head = null;
    DLL tail = null;
    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.map = new HashMap<>();
    }
    
    public int get(int key) {
        if(!map.containsKey(key))
            return -1;
        DLL node = map.get(key);
        removeNode(node);
        insertNode(node);
        return node.val;   
    }
    
    public void put(int key, int value) {
        if(map.containsKey(key)){
            DLL node = map.get(key);
            node.val = value;
            removeNode(node);
            insertNode(node);
        }
        else{ 
            if(map.size()==capacity){
                map.remove(tail.key);
                removeNode(tail);
            }
            DLL node = new DLL(key, value);
            insertNode(node);
            map.put(key,node); 
        }       
    }


    public void removeNode(DLL node){
        if(node.prev!=null) node.prev.next = node.next;
        else head = node.next;
        if(node.next!=null) node.next.prev = node.prev;
        else tail = node.prev;
    }

    public void insertNode(DLL node){
        node.prev = null;
        node.next = head;
        if(head!=null)
            head.prev = node;
        head = node;
        if(tail==null) tail = node;
    }
}

class DLL{
    DLL prev, next;
    int key, val;
    public DLL(int key, int val){
        this.key = key;
        this.val = val;
    }
}
```
### Time Complexity: O(1)
### Space Complexity: O(n+n)