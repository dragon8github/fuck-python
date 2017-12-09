# 函数的定义和参数

https://docs.python.org/3.7/tutorial/controlflow.html\#defining-functions

https://docs.python.org/3.7/tutorial/controlflow.html\#more-on-defining-functions

#### 不定数参数

```py
# -*- coding: utf-8 -*-
def showme(name, *info):
    print(name)

    for a in info:
        print(a)

showme("Lee", 1,2,3,4)
```

![](/assets/231212import.png)

#### 关键字参数

```py
# -*- coding: utf-8 -*-
def showme(name, *info, **info2):
    print(name, info)

    for b in info2:
        print(b, info2[b])


showme("Lee", 1,2,3,4,age=12,sex='女')
```

![](/assets/211515123import.png)

#### 获取参数类型

```py
# -*- coding: utf-8 -*-
def showme(name, *info, **info2):
    print(type(name))
    print(type(info))
    print(type(info2))

showme("Lee", 1, 2, 3, 4, age=12, sex='女')
```

![](/assets/124112import.png)

---

### 强大到令人发指的Data Structures

[https://docs.python.org/3/tutorial/datastructures.html](https://docs.python.org/3/tutorial/datastructures.html)

![](/assets/15123123import.png)

---

### **range函数的使用**

```py
items=[]
for x in range(0, 10):
    items.append(x)

print(items) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

###################################################

items=[]
for x in range(10, 0, -1):
    items.append(x)

print(items) # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]

#####################################################

print(list(range(0, 10))) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

#####################################################

item=[a**2 for a in range(0, 10, 2)]
print(item) # [0, 4, 16, 36, 64]

#####################################################

# center right left
item=[a**2 for a in range(0, 10, 2) if a>4]
print(item) # [36, 64]
```



