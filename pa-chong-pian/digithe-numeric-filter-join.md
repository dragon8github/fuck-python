### 判断是否为数字：digit 和 numeric

```py
print('4'.isdigit())  true
print('四'.isdigit()) false

print('4'.isnumeric()) true
print('四'.isnumeric()) true
```

---

### filter 函数 与 lambda表达式

```py
def isInt(item):
    return item.isdigit()

print(filter(isInt, 'ab123ef'))       # <filter object at 0x00535350>
print(list(filter(isInt, 'ab123ef'))) # 小技巧，使用强制转化为list可以输出内容：['1', '2', '3']

# 使用 lambda 表达式可以抒写匿名函数
print(list(filter(lambda x: x.isdigit(), 'ab123ef'))) # ['1', '2', '3']
```

---

#### join 函数：将数组转化为字符串

```
print('-'.join(filter(lambda x:x.isdigit(),'ab123ef'))) # 1-2-3
```



