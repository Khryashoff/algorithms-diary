## Move Zeroes - Leetcode 283. Easy

Учитывая массив целых чисел, nums переместите все 0 в конец его, сохраняя относительный порядок ненулевых элементов.

Обратите внимание, что вы должны сделать это на месте, не создавая копию массива.

**Пример 1:**
```bash
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```
**Пример 2:**
```bash
Input: nums = [0]
Output: [0]
```
**Пример 3:**
```bash
Input: nums = [0,0,4,5,0,0]
Output: [4,5,0,0,0,0]
```


**Решение 1** - Время 105 мс (лучше ~96,83%), память 12.75 MB (лучше ~87,33%)
```python
class Solution(object):
    def moveZeroes(self, nums):
        freeIdx = 0
        
        for i in range(len(nums)):
            if nums[i] != 0:
                nums[freeIdx] = nums[i]
                freeIdx += 1
        
        for i in range(freeIdx, len(nums)):
            nums[i] = 0
```

**Решение 2** - Время 110 мс (лучше ~88,04%), память 12.68 MB (лучше ~97,44%)
```python
class Solution(object):
    def moveZeroes(self, nums):
        freeInd = 0

        for num in nums:
            if num == 0:
                continue
            nums[freeInd] = num
            freeInd += 1 
        for i in range(freeInd, len(nums)):
            nums[i] = 0
```

**Оценка по времени:** O(n)  
Осуществляется два прохода по исходному массиву в отдельных циклах.

**Оценка по памяти:** O(1)  
Объявляется одна переменная хранящая текущее свободное место для перемещения пространство, дополнительная память не используется, все перестановки происходят внутри исходного массива.  

**Объяснение решения**  
1. Инициализируется одна переменная для хранения текущего свободного индекса. 
2. Запускается цикл, который работает с диапазоном индексов равным длине массива nums -1. Если число с индексом i не равно нулю, то оно перезаписывается на позицию со свободным индексом. К позиции свободного индекса прибавляется единица +1.
3. Запускается цикл, который перебирает диапазон оставшихся чисел от текущего свободного индекса до конца массива nums. Всем числам в этом диапазоне присваивается значение ноль 0.
4. Входящий массив возвращается самостоятельно.
