# Question

We are given an array asteroids of integers representing asteroids in a row. The indices of the asteriod in the array represent their relative position in space.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.


##### Example:

Input: asteroids = [5,10,-5]

Output: [5,10]

Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.



### Solve: [https://leetcode.com/problems/asteroid-collision/](https://leetcode.com/problems/asteroid-collision/)
   


# Optimal Solution:  


``` java
    public int[] asteroidCollision(int[] asteroids) {
        ArrayDeque<Integer> st = new ArrayDeque<>();
        for(int i : asteroids){
            boolean alive = true;
            while(alive && !st.isEmpty() && st.peek()>0 && i<0){
                if(Math.abs(st.peek())==Math.abs(i)){
                    st.pop();
                    alive = false;
                }
                else if(Math.abs(st.peek())<Math.abs(i)){
                    st.pop();
                }
                else{
                    alive = false;
                }
            }
            if(alive)
                st.push(i);
        }
        int res[] = new int[st.size()];
        for(int i=res.length-1;i>=0;--i){
            res[i] = st.pop();
        }
        return res;
    }
```
### Time Complexity: O(3n)
### Space Complexity: O(2n)