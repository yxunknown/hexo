---
title: Python集合操作
date: 2019-03-20 21:42:02
tags: 
- Python
- collections
categories: Pythonic
---

> **注意:**文中代码环境为`Python 3.6.3`

# filter

filiter用于对一个集合进行过滤，收集满足条件的元素并返回一个新的列表。

```python
nums = [x for x in range(10)]
odds = filter(lambda num: num % 2 != 0, nums)
print odds
# [1, 3, 5, 7, 9]
```

filter函数接受两个参数，第一个参数为过滤函数，第二个参数是一个Iterable；而第一个参数的定义如下：

```python
def f(x):
    # checks on x
    # wheather x be selected
    return True
```

# map

map函数能够对一个Iterable内的每一个元素都执行一遍同一个操作，而这个操作就由传递给map函数的函数参数来定义：

```python
nums = [x for x in range(5)]
nums_time_2 = map(lambda x: x * 2, nums)
print nums_time_2
# [0, 2, 4, 6, 8]
```

map函数还能传递多个Iterable参数，此时操作函数能接受的参数个数与Iterable的个数对应，如：

```python
a = [1, 3, 5, 7, 9]
b = [2, 4, 6, 8, 10]
a_plus_b = map(lambda x, y: x + y, a, b)
print a_plus_b
# [3, 7, 11, 15, 19]
```

# sort

sort可以对Iterable进行排序，python内置了sorted函数。但有一点应该注意的是，对于list类型的对象，python还提供了sort方法。

```python
mans = [{
    "name": "ipad",
    "age": 4
}, {
    "name": "iphone",
    "age": 10
}, {
    "name": "laptop",
    "age": 20
}, {
    "name": "wifi",
    "age": 15
}]
sorted_mans = sorted(mans, lambda m: m["age"], reverse=True)
# 以age的值作为排序关键字，结果为降序
# 等价代码
mans.sort(lambda m: m["age"], reverse=True)
```

sorted排序的结果默认是升序。在Python2.X中，sorted函数还有一个cmp的参数，可以自定义比较行为；但Python3.X中sorted函数的cmp参数已经不见踪影，为什么呢？

Python是一门神奇的语言，嗯.....(别无解释)。若不是目前跟的项目是Python开发的，我想我的一生中怎么也不会用Python正儿八经的写代码吧。毕竟对Python这种弱类型语言嗤之以鼻；我认同Python的语法简洁也很高效，语句功能强大。但是这东西自己写的时候很爽，去维护别人的代码的时候Python代码的可读性和可维护性不够好。尤其是对于习惯于Ctrl+B跳转的孩子来说，太残忍了那就。一个方法里面，你看着一个参数，参数也看着你，可是你们之间不会产生任何的心灵感应；不一会，屏幕前的你就已经睡着了！

