### 不定数参数

```py
# -*- coding: utf-8 -*-
def showme(name, *info):
    print(name)

    for a in info:
        print(a)

showme("Lee", 1,2,3,4)
```

![](/assets/231212import.png)

### 关键字参数

```py
# -*- coding: utf-8 -*-
def showme(name, *info, **info2):
    print(name, info)

    for b in info2:
        print(b, info2[b])


showme("Lee", 1,2,3,4,age=12,sex='女')
```

![](/assets/211515123import.png)

### 获取参数类型

```py
# -*- coding: utf-8 -*-
def showme(name, *info, **info2):
    print(type(name))
    print(type(info))
    print(type(info2))

showme("Lee", 1, 2, 3, 4, age=12, sex='女')

```

![](/assets/124112import.png)

