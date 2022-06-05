# Climb the staircases
## Discription
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

> Input: n = 2. 
> Output: 2.   
> Explanation: There are two ways to climb to the top.  
> 1.  1 step + 1 step. 
> 2.  2 steps. 

### The first solution 
```python

class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1 or n == 2:
            return n
        a,b,temp = 1,2,0

        #continue calculate the digits
        for i in range(3,n+1):
            temp = a+b 
            a = b
            b = temp
        return temp

```
> This is the simple way of using Fibonacci 
