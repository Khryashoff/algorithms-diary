## Search a 2D Matrix - Leetcode 74. Medium

Вам будет предоставлена m x n целочисленная матрица matrix со следующими двумя свойствами:
- Каждая строка сортируется в неубывающем порядке.
- Первое целое число каждой строки больше последнего целого числа предыдущей строки.

По заданному целому числу target верните значение, true если target находится в matrix или false иначе.

Вы должны написать решение с O(log(m * n)) временной сложностью.

**Пример 1:**
```bash
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: True
```
**Пример 2:**
```bash
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: False
```

**Решение 1** - время 30 мс (лучше ~99.71%), память 17,03 MB (лучше ~67.08%)
```python
class Solution:
    def good(self, val:int, target:int) -> bool:
        return val <= target

    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        left = 0
        right = len(matrix) * len(matrix[0])
        length = len(matrix[0])
        
        while right - left > 1:
            current = (left + right) // 2
            n = current // length
            m = current % length
            if self.good(matrix[n][m], target):
                left = current
            else:
                right = current
        left_n = left // length
        left_m = left % length
        return matrix[left_n][left_m] == target
```

**Решение 2** - время 44 мс (лучше ~67.86%), память 17,23 MB (лучше ~24.65%)
```python
class Solution:

    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        def elementFromMatrix(i: int):
            n = len(matrix[0])
            return matrix[i // n][i % n]

        def good(i: int):
            return elementFromMatrix(i) <= target

        left = 0
        right = len(matrix) * len(matrix[0])
        while right - left > 1:
            m = (left + right) // 2
            if good(m):
                left = m
            else:
                right = m
        return elementFromMatrix(left) == target
```

**Оценка по времени:** O(log n*m)  
Осуществляется бинарный поиск по исходной матрице, где n - длина строки, а m - высота столбца.

**Оценка по памяти:** O(1)  
Аллоцируемая дополнительная память на хранение переменных является константной, т.к. меньше размера исходной матрицы.

**Объяснение решения**  
1. В основной функции searchMatrix создаются три переменных для хранения текущего положения правого и левого индексов, а также длины строки матрицы.
2. Запускается цикл, который работает, пока разность правого и левого индексов больше единицы.
3. Создается проверочное выражение для получения среднего индекса путем деления суммы текущих индексов на два // 2.
4. Производится расчёт положения среднего индекса в матрице (получение n & m).
5. Запускается дополнительная функция good, которая сравнивает значения и возвращает True или False. 
Если значение matrix с текущим индексом меньше или равно целевому числу, то указатель левого индекса принимает значение текущего индекса.
6. Иначе, правый индекс принимает значение среднего индекса.
7. Производится расчёт положения последнего левого индекса и возвращается True если значение matrix левого индекса равно целевому числу, иначе возвращается False. 
