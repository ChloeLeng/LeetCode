# Discription
Given an array of size n, find the majority element. The majority element is the element that appears more than floor(n/2) times.
You may assume that the array is non-empty and the majority element always exist in the array.

Example :

Input : [2, 1, 2]
Return  : 2 which occurs 2 times which is greater than 3/2.

## 思路解析
这道题就是求List中的众数

### 摩尔投票
> 最开始想到的方法是Boyer-Moore投票算法 （摩尔投票法）：  
> 题目中我们需要查找的数字超过数组长度的一半，我们就可以使用摩尔投票法： 假设不同的数字相抵消，那么最后剩下的数字，就是我们要找的多数元素

We can assume the first number in the list to be target, and then go through the list, we try to use the counter to simulate this process.  
1. When the element != target, counter -= 1, 即模拟不同的数字相抵消  
2. When the element  == target, counter += 1. 
3. When counter == 0, 说明在档案遍历到的数组元素中，当前假设的target和其他数字相互抵消，所以我们重新假设下一个便利的数组元素为target，继续上面过程

```python
def majorityElement(self, A):
        major, count = 0, 0
        for n in A:
            if count == 0:
                major = n
            if n == major:
                count += 1
            else:
                count -= 1
        return major
```
