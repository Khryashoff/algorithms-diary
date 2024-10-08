## Middle of the Linked List - Leetcode 876. Easy

Учитывая head односвязный список, верните средний узел связанного списка.

Если есть два средних узла, верните второй средний узел.

**Пример 1:**
```bash
Input: head = [1,2,3,4,5]
Output: [3,4,5]
```
**Пример 2:**
```bash
Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
```

**Решение**
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head
        
        while fast is not None and fast.next is not None:
                fast = fast.next.next
                slow = slow.next
        return slow
```

**Оценка по времени:** O(n)  
Осуществляется один проход по исходному массиву.

**Оценка по памяти:** O(1)  
Аллоцируемая дополнительная память на хранение переменных является константной, т.к. меньше размера исходного массива.

**Объяснение решения**  
1. Создаются две переменные для хранения значений быстрого и медленного указателей.
2. Запускается цикл, который работает, пока текущее значение не равно None и следующее после текущего значения не равно None.
3. Быстрому указателю присваивается значение через один элемент после текущего.
4. Медленному указателю присваивается значение следующего элемента после текущего.
5. Возвращается значение медленного указателя, т.к. он занял среднее положение в связанном списке.
