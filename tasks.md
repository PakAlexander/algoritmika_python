# Задача 1
**Функция создания словаря из строки:
def get_dict(str):... Возвращает словарь.
Строка имеет формат: str = "one=1 two=2 three=3"
Значениями должны быть целые числа.
Пример: 
"one=1 two=2 three=3" -> {'one': 1, 'two': 2, 'three': 3}**

Решение:
Вариант 1(цикл for):
```
def get_dict(str):
    str, res = str.split(), []
    for i in str:
        el = i.split('=')
        el[1] = int(el[1])
        res.append(el)
    return dict(res)
    
str = "one=1 two=2 three=3"
print(get_dict(str))    
```
Вариант 2(Генератор списков):
```
def get_dict(ls):
    str = ls.split()
    str = [i.split('=') for i in str]
    return {val[0]: int(val[1]) for val in str}

str = "one=1 two=2 three=3"
print(get_dict(str))
```

# Задача 2

**Функуция получает строку в формате ключ=значение в одну строчку через пробел.
Необходимо на их основе создать словарь d, затем удалить из этого словаря ключи 'False' и '3', если они существуют. Ключами и значениями словаря являются строки. Для вывода используйте функцию print. Функция ничего возвращать не должна.
Пример:"лена=имя дон=река москва=город False=ложь 3=удовлетворительно True=истина" -> {'лена': 'имя', 'дон': 'река', 'москва': 'город', 'True': 'истина'}**

Решение:
Вариант 1(цикл for):
```
def get_dict(ls):
    ls, res = ls.split(), []
    for i in ls:
        el = i.split('=')
        if el[0] not in ["False", "3"]:
            res.append(el)
    print(dict(res))
    
ls = "лена=имя дон=река москва=город False=ложь 3=удовлетворительно True=истина"
get_dict(ls)
```
Вариант 2(Генератор списков):
```
def get_dict(ls):
    ls = ls.split()
    d = dict([i.split('=') for i in ls])
    d = {k: v for k, v in d.items() if k not in ["False", "3"]}
    print(d)

ls = "лена=имя дон=река москва=город False=ложь 3=удовлетворительно True=истина"
get_dict(ls)
```
