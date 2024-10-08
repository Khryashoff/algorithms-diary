## Хэш-таблицы

**Паттерны хэш-таблицы**

Хэш-таблицы можно поделить на два лагеря:
- Постепенное заполнение
- Предварительное заполнение

*Постепенное заполнение* - когда осуществляется проход по массиву, в него закладывается очередной новый элемент и производятся некоторые проверки. Подобный принцип встречается в задачах:
- Сумма двух чисел
- Изоморфные строки
- Правильное судоку

*Предварительное заполнение* - когда не производятся какие либо проверки, а осуществляется предварительное перенесение данных из какой-либо структуры данных (чаще всего из массива) в хэш-таблицу. Подобный принцип встречается в задачах:
- Поиск оси симметрии

Дополнительно к этому можно выделить такие паттерны как:
- Mapping
- Ключ-количество и количество-ключ
- Подсчет элементов
