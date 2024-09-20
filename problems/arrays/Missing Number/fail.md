Изначальная очень грубая версия, которая не учитывала множество краевых случаев. Изначально понимал, что код не жизнеспособен, но было интересно его "проапгрейдить", чтобы он проходил хотя бы часть тестов. 

**Решение 1**
```python
class Solution(object):
    def missingNumber(self, nums):
        big = 0
        prefix_sum = 0
        
        for i in nums:
            if i > big:
                big = i
            prefix_sum += i
            
        total_sum = sum(range(big))
        n = total_sum - prefix_sum
        return n
```

Настоящий франкенштейн получившийся после нескольких итераций и исправлений. Проваливался на проверке nums = [1,2]. После этого решил прекратить его мучения. 

**Решение 2**
```python
class Solution(object):
    def missingNumber(self, nums):
        big = 0
        prefix_sum = 0
        
        for i in nums:
            prefix_sum += i
            if i >= big:
                big = i  
            
        total_sum = sum(range(big+1))
        if len(nums) == 1 and big == 1:
            n = 0
        elif len(nums) == 1 and big == 0:
            n = 1
        elif total_sum == prefix_sum:
            big +=1
            total_sum = sum(range(big+1))
            n = total_sum - prefix_sum
        else:
            n = total_sum - prefix_sum
        return n
```
