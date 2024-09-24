Довольно глупая ошибка, но как есть. В sum (тоже не совсем удачное название для переменной) складываю индексы вместо чисел из массива.

```python
class Solution(object):
    def twoSum(self, numbers, target):
        left = 0
        right = len(numbers) - 1
        
        while left < right:
            sum = left + right
            if sum == target:
                return(left + 1, right + 1)
            elif sum < target:
                left += 1
            else:
                right -= 1
```
