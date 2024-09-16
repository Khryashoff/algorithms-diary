Была проявлена невнимательность и упущен краевой случай, когда самое максимальное значение может находиться в самом начале, например nums = [10,2,5,2].
В таком случае конструкция не проходит дальнейшую проверку из-за условия 'and', так как значение i должно удовлетворять сразу двум условиям. 

```python
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        max_val = 0
        second_max_val = 0
        
        for i in nums:
            if i >= max_val and i >= second_max_val:
                second_max_val = max_val
                max_val = i
        return(max_val - 1)*(second_max_val - 1)
```
