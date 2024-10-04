## Reverse Linked List - Leetcode 206. Easy

Учитывая head односвязный список, переверните список и верните перевернутый список.

**Пример 1:**
```bash
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```
**Пример 2:**
```bash
Input: head = [1,2]
Output: [2,1]
```
**Пример 3:**
```bash
Input: head = []
Output: []
```


**Решение**
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        previous = None
        current = head
        
        while current is not None:
            next_node = current.next
            current.next = previous
            previous = current
            current = next_node
        return previous 
```

**Оценка по времени:** O(n)  
Осуществляется один проход по исходному массиву.

**Оценка по памяти:** O(1)  
Аллоцируемая дополнительная память на хранение переменных является константной, т.к. меньше размера исходного массива.

**Объяснение решения**  
1. Создаются переменные для хранения предыдущего и текущего значения.
2. Запускается цикл, который работает, пока текущее значение не равно None.
3. Создается переменная хранящее следующее после текущего значение. 
4. Следующему текущему значению присваивается предыдущее значение.
5. Предыдущему значению присваивается текущее значение.
6. Текущему значению присваивается сохраненное заранее следующее значение.
7. Возвращается переменная хранящее предыдущее значение, которое в результате перестановок заменило первое значение.

Далее приведены мои рассуждения на гипотетическом примере.  

head = [1 -> 2 -> 3 -> 4 -> None]    

next_node = 2  
current.next = None  
previos = 1  
current = 2  

[None <- 1 2 -> 3 -> 4 -> None]  

next_node = 3  
current.next = 1  
previous = 2  
current = 3  

[None <- 1 <- 2 3 -> 4 -> None]  

...  

next_node = None  
current.next = 3  
previous = 4  
current = None  

[None <- 1 <- 2 <- 3 <- 4]  
