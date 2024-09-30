Код в целом был неплох, но была проблема, когда правый индекс пытался выбраться за пределы исходного массива. Пришлось внести поправки в эту строку: "if indRight + 1 < len(nums) and nextIdx == nums[indRight + 1]:". Важно, чтобы проверка знака меньшенства находилась впереди равенства. Также оказывается f-строку добавили только в 3 версию Python. Пытался решать на 2, а оно не работало, долго не мог понять почему. 

```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        indLeft = 0
        indRight = 0
        result = []
        
        while indLeft < len(nums):
            nextIdx = nums[indRight] + 1
            if nextIdx == nums[indRight + 1]:
                indRight += 1
                continue
            else:
                if indLeft != indRight:
                    result.append(f'{nums[indLeft]}->{nums[indRight]}')
                else:
                    result.append(f'{nums[indRight]}')
            indLeft = indRight + 1
            indRight += 1
        return result
```
