## Find First and Last Position of Element in Sorted Array - Leetcode 34. Medium

Дан массив целых чисел nums, отсортированный в порядке неубывания, найдите начальную и конечную позиции заданного значения target.

Если target не найден в массиве, верните [-1, -1].

Вы должны написать алгоритм со O(log n) сложностью во время выполнения.

**Пример 1:**
```bash
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```
**Пример 2:**
```bash
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```
**Пример 3:**
```bash
Input: nums = [], target = 0
Output: [-1,-1]
```


**Решение 1** - время 74 мс (лучше ~66.29%), память 17,89 MB (лучше ~50.84%)
```python
class Solution:
    def good(self, val:int, target:int) -> bool:
        return val <= target

    def goodTwo(self, val:int, target:int) -> bool:
        return val < target

    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if len(nums) == 0:
            return -1, -1
        left = 0
        right = len(nums)

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
            if self.goodTwo(nums[curr], target):
                left = curr
            else:
                right = curr
        first = right
        return first, last
```

**Решение 2** - время 44 мс (лучше ~67.86%), память 17,23 MB (лучше ~24.65%)
```python
class Solution:
    def search_last_target(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums)
        while right - left > 1:
            m = (left + right) // 2
            if nums[m] <= target:
               left = m
            else:
               right = m
        return left if nums[left] == target else -1
    
    def search_first_target(self, nums: List[int], target: int) -> int:
        left, right = -1, len(nums) - 1
        while right - left > 1:
            m = (left + r) // 2
            if nums[m] < target:
               left = m
            else:
               right = m
        return right if nums[right] == target else -1


    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if len(nums) == 0:
            return [-1, -1]
        left = self.search_first_target(nums, target)
        right = self.search_last_target(nums, target)
        return [left, right]
```

**Оценка по времени:** O(log n)  
Осуществляется бинарный поиск по исходному массиву.

**Оценка по памяти:** O(1)  
Аллоцируемая дополнительная память на хранение переменных является константной, т.к. меньше размера исходного массива.

**Объяснение решения**  
1. В основной функции searchRange осуществляется проверка на пустой массив, если это так возвращается -1, -1. Создаются две переменных для хранения текущего положения правого и левого индексов.
2. Запускается цикл, который работает пока пока разность правого и левого индексов больше единицы.
3. Производится расчёт положения среднего индекса в массиве.
4. Запускается первая дополнительная функция good, которая сравнивает значения и возвращает True или False. 
Если значение nums с текущим средним индексом меньше или равно целевому числу, то указатель левого индекса принимает значение среднего индекса.
5. Иначе, правый индекс принимает значение среднего индекса.
6. Если полученное значение nums с индексом left не равно целевому числу, то возвращается -1, -1. 
7. Создается переменная для хранения последнего вхождения, а значение левого и правого индексов обновляется.
8. Запускается цикл, который работает пока пока разность правого и левого индексов больше единицы.
9. Запускается вторая дополнительная функция goodTwo, которая сравнивает значения и возвращает True или False. 
Если значение nums с текущим средним индексом меньше целевого числа, то указатель левого индекса принимает значение среднего индекса.
10. Иначе, правый индекс принимает значение среднего индекса.
11. Создается переменная для хранения первого вхождения. Возвращает результат - индексы первого и последнего вхождения целевого числа в массиве. 
