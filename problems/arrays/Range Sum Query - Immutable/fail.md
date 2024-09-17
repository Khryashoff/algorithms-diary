Не использовал self для сохранения атрибута объекта, а пытался просто вернуть полученный массив arr.
В целом решение выглядит менее изящно из-за использования дополнительных переменных.

```python
class NumArray(object):

    def __init__(self, nums):
        arr = [0]
        for i in range(0, len(nums)): 
            n = arr[i] + nums[i]
            arr.append(n)
        return arr
        

    def sumRange(self, left, right):
        sum = arr[right+1] - arr[left]
        return sum
```
