# Python排序快速入门, list.sort() 与 sorted()的不同

> 原文: [https://www.30secondsofcode.org/articles/s/python-sortedlist-vs-list-sort](https://www.30secondsofcode.org/articles/s/python-sortedlist-vs-list-sort)

Python提供了两种列表排序方法：

1. `list.sort()`
2. `sorted()`

## 1. 不同

不同的地方主要有两点：

1. `list.sort()`：直接对**列表**进行排序，并返回`None`，
`sorted()`：返回排序后的列表，不更改原列表；
2. `list.sort()`是`列表list`的方法，`sorted()`可对任意**可迭代**的对象进行排序。

```python
nums = [2, 3, 1, 5, 6, 4, 0]

'''sorted返回新列表，不更改原列表'''
print(sorted(nums))   # [0, 1, 2, 3, 4, 5, 6]
print(nums)           # [2, 3, 1, 5, 6, 4, 0]

'''list.sort()返回None，但是更改原列表'''
print(nums.sort())    # None
print(nums)           # [0, 1, 2, 3, 4, 5, 6]

'''sorted()可以对可迭代的对象进行排序'''
nums = (2, 3, 1, 5, 6, 4, 0)
print(sorted(nums))   # [0, 1, 2, 3, 4, 5, 6]
print(nums.sort())    # 报错
```

## 2. 相同

二者都可以传入`key`与`reverse`两个参数。

1. `key`: 用来比较的参数
2. `reverse`: True->降序, False->升序

```python
# 获取元素的第二个元素
def takeSecond(elem):
    return elem[1]
 
# 列表
random = [(2, 2), (3, 4), (4, 1), (1, 3)]
 
# 指定第二个元素排序
print(sorted(random, key=takeSecond)) # [(4, 1), (2, 2), (1, 3), (3, 4)]
print(sorted(random, key=lambda x: x[1])) # key的lambda写法, 输出: [(4, 1), (2, 2), (1, 3), (3, 4)]
print(sorted(random, key=takeSecond, reverse=True)) # [(3, 4), (1, 3), (2, 2), (4, 1)]
random.sort(key=takeSecond)
print(random) # [(4, 1), (2, 2), (1, 3), (3, 4)]
```

## 3. 怎么用

1. `list.sort()`：对列表进行排序的时候用
2. `sorted()`：对可迭代的对象（例如：列表、元组、字典、字符串）进行排序，且期望列表包含所有元素