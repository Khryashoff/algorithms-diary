## Subarray Sum Equals K - Leetcode 560. Medium

Учитывая массив целых чисел nums и целое число k, верните общее количество подмассивов, сумма которых равна k.

Подмассив - это непрерывная непустая последовательность элементов в массиве.

**Пример 1:**
```bash
Input: nums = [1,1,1], k = 2
Output: 2
```

**Пример 2:**
```bash
Input: nums = [1,2,3], k = 3
Output: 2
```

**Пример 3:**
```bash
Input: nums = [0,0,0,0], k = 0
Output: 10
```


**Решение**
```python
class Solution(object):
    def subarraySum(self, nums, k):
        prefix_sum = {0:1}
        current_prefix_sum = 0
        count = 0
        
        for i in nums:
            current_prefix_sum += i
        
            if (current_prefix_sum - k) in prefix_sum:
                count += prefix_sum[current_prefix_sum - k]
            
            if current_prefix_sum not in prefix_sum:
                prefix_sum[current_prefix_sum] = 0
            prefix_sum[current_prefix_sum] += 1
        
        return count
```

**Оценка по времени:** O(n)  
Осуществляется один проход по исходному массиву.  
**Оценка по памяти:** O(n)  
Создается хэщ-таблица prefix_sum, в худшем случае, если все элементы будут уникальны, то его длина будет n.

**Объяснение решения**  
1. Инициализируется префиксная хэш-таблица для хранения суммируемых значений, где ключ - префиксная сумма, а значение - количество встреченных раз.
Счетчик текущей префиксной суммы и результирующий счетчик.
2. Запускается цикл, в котором к счетчику текущей префиксной суммы прибавляется текущее значение из массива nums. 
3. Если разность текущей префиксной суммы и целевого числа k есть в префиксной хэш-таблице, то к счетчику прибавляется значение ключа из префиксной хэш-таблицы.
4. Если текущая префиксная сумма отсутствует в префиксной хэш-таблице, то создается ключ [текущая префиксная сумма] со значением 0. 
К ключу текущей префиксной суммы добавляется 1.
5. Возвращается результат - количество подмассивов, сумма которых равна k.
