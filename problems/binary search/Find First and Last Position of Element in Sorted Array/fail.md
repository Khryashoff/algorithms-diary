Был ещё более нерабочий вариант решения, но он к сожалению утрачен для истории. В нём я пытался решить всё при помощи одной дополнительной функции с проверкой, но вариант не жизнеспособный. По ошибкам:
1. Отсутствует проверка, если входной массив пустой.
2. При поиске первоначального вхождения, запрос отправляется не в функцию goodTwo, а в good.

```python
class Solution:
    def good(self, val:int, target:int) -> bool:
        return val <= target

    def goodTwo(self, val:int, target:int) -> bool:
        return val < target

    def searchRange(self, nums: List[int], target: int) -> List[int]:
        left = 0
        right = len(nums)
        # Здесь нет проверки
        while right - left > 1:
            curr = (left + right) // 2
            if self.good(nums[curr], target):
                left = curr
            else:
                right = curr
        if nums[left] != target:
            return -1, -1
        last = left
        right = left
        left = -1
        while right - left > 1:
            curr = (left + right) // 2
            # Здесь неверная передача названия функции
            if self.good(nums[curr], target):
                left = curr
            else:
                right = curr
        first = right
        return first, last
```
