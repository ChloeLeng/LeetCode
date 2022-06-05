## Problem discription
You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

### Example
Input: digits = [1,2,3]  
Output: [1,2,4]。
Explanation: The array represents the integer 123.  
Incrementing by one gives 123 + 1 = 124.  
Thus, the result should be [1,2,4].  

Input: digits = [4,3,2,1]  
Output: [4,3,2,2]  
Explanation: The array represents the integer 4321.  
Incrementing by one gives 4321 + 1 = 4322.  
Thus, the result should be [4,3,2,2].  

Input: digits = [9]  
Output: [1,0]  
Explanation: The array represents the integer 9.  
Incrementing by one gives 9 + 1 = 10.  
Thus, the result should be [1,0].  


```python

class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
               # we have to find the first non-nine digit number in the list by reverse the list
        n = len(digits)
        for i in range(n-1,-1,-1):
            if digits[i] != 9:
                digits[i]+=1
                for j in range(i+1,n):
                    digits[j]=0
                return digits
            #The last condition is that all the digits are 9, so we just construct another new list
        return [1]+[0]*n
            
```
