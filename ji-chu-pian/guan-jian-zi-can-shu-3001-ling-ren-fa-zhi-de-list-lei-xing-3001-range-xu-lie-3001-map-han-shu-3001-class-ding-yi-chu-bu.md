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

