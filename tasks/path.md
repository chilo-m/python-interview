Канонический путь
```
Дан абсолютный путь от рута до файла или каталога в UNIX системе. Требуется привести его к каноническому виду.

Канонический вид:

Путь начинается с '/'.
Путь не заканчивается на '/'.
Два каталога разделены одинарным '/'.
Путь содержит только каталоги на пути от root до target файла или каталога
Примеры:

/home/ -> /home
/../ -> /
/../abc//./def/ -> /abc/def
/a/b/c/../.. -> /a
```
Решение python
```python
def canonical_path(path: str) -> str:
    parts = path.split('/')
    stack = []
    for part in parts:
        if part == '' or part == '.':
            continue
        elif part == '..':
            if stack:
                stack.pop()
        else:
            stack.append(part)
    return '/' + '/'.join(stack)
```
