В целом было неплохо написано, однако есть несколько недочётов из-за которых ничего не работало.  
Во-первых, я упорно забываю заключать сумму в этом выражении в скобки current = left + right // 2, это уже повторяется во второй раз.  
Во-вторых, я зачем-то суммирую значения в цикле while right + left > 1, вместо вычитания.  
Виновник третьей ошибки - чатгпт, который ввёл меня в заблуждение, что len(matrix) рассчитывает длину строки, хотя на самом деле оно определяет высоту столбца.

```python
class Solution:
    def good(self, val:int, target:int) -> bool:
        return val <= target

    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        left = 0
        right = len(matrix) * len(matrix[0])
        
        while right + left > 1:
            current = left + right // 2
            n = current // len(matrix)
            m = current % len(matrix)
            if self.good(matrix[n][m], target):
                left = current
            else:
                right = current
        left_n = left // len(matrix)
        left_m = left % len(matrix)
        return matrix[left_n][left_m] == target
```
