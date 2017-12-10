### 多版本共存的小技巧

比如你当前系统变量配置的python版本是2.7，那么你再下载一个3.6，并且照样加入到系统变量中，只是把3.6目录下的python.exe改为python36即可。这样你在cmd中只要输入python36即可进入版本。这是一个无脑的小技巧罢了。

---

## 模块的导入

[https://docs.python.org/3/tutorial/modules.html](https://docs.python.org/3/tutorial/modules.html)

在python中任何一个文件都可以看做一个模块。

新建一个functions.py

```py
name = 'Lee'

def show():
    print(name)

print('versions is 1.0')
```

回到我们的主模块main.py

```py
import functions  # versions is 1.0

functions.show() # Lee

print(functions.name) # Lee
```

我们可以看出，Import 模块之后，不仅会执行模块中的内容，如Print。

其次是可以使用模块中的全局变量、方法。

### import from 语法的使用

```py
from functions import show,name # versions is 1.0

show() # Lee

print(name) # Lee
```

---



