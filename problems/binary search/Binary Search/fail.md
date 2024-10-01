В моей теории это даже работало, пока не столкнулось с суровой реальностью)) Из ошибок: 
1. Неправильный цикл while, который не предусматривал возможное сужение указателей, а следовательно запускался неправильно. 
2. Логика сравнения описана верно, но её лучше вынести в отдельную функцию, чтобы проще было менять условия для сравнения и это хорошо с точки зрения абстрации. 
3. Внутренняя проверка равенства с целевым числом тоже работала не правильно, не был рассмотрен случай, когда должна была возвращаться -1.

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums)
        
        while left < len(nums):
            current = left + right // 2
            if nums[current] <= target:
                left = current
                if nums[current] == target:
                    return current
            else:
                right = current
```

Следующая итерация без функции good для обработки равенства и с менее красивым возвратом полученного результата.

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums)
        
        while right - left > 1:
            current = (left + right) // 2
            if nums[current] <= target:
                left = current
            else:
                right = current 
        if nums[left] == target:
            return left
        else:
            return -1
```
