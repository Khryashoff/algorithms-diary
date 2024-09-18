Мертворожденная версия в которой были допущены ошибки в равенстве, вместо '==', было присвоение '=', а также вместо nums[i], передавалось просто i.
Кроме этого была ошибка с выводом индекса, здесь как раз наоборот было nums[i], вместо i.

```python
class Solution(object):
    def pivotIndex(self, nums):
        prefix_arr = 0
        right_sum = 0
        left_sum = 0 
        
        for i in nums:
            prefix_arr += i
        
        for i in nums:
            right_sum = prefix_arr - left_sum - i
            if left_sum = right_sum:
                return nums[i]
            elif left_sum < right_sum:
                left_sum += i
            else:
                return -1
```

Улчшенный вариант, но он проваливал тест, где значения были отрицательные, например nums = [-1, -1, -1, -1, -1, 0]. 
Потребовалось вынести возвращение -1 из цикла, а также заменить конструкцию elif на else, который бы позволял корректно обрабатывать вышепреведенный случай.

```python
class Solution(object):
    def pivotIndex(self, nums):
        prefix_arr = 0
        right_sum = 0
        left_sum = 0 
        
        for i in nums:
            prefix_arr += i
        
        for i in range(0, len(nums)):
            right_sum = prefix_arr - left_sum - nums[i]
            if left_sum == right_sum:
                return i
            elif left_sum < right_sum:
                left_sum += i
            else:
                return -1
```
