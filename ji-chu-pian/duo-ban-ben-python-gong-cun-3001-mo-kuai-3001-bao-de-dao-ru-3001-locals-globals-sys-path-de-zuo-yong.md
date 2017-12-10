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

### （package）包的创建和导入

任何一个文件夹都可以为包，只是需要包含**init**.py这样的文件即可。，譬如我们可以创建一个Common的模块。

![](/assets/123123123import.png)

一个包就创建完成了，引入有很多种方式，我们一一来看看：

**1、导入指定函数 / 变量**

```py
from Common.functions import show  # versions is 1.0
 
show() # Lee
```

**2、无脑引入法**

```py
import Common.functions # versions is 1.0
 
Common.functions.show() # Lee
```

---

### 包使用 all 控制模块的导出

如果我们的模块或包只想暴露出指定的方法给外部呢？其他不允许访问。这应该如何设置？就要用到如下配置了。

在init.py文件中如下配置，这样外部只能引用functions这个库了

```py
__all__ = ["functions"]
```

### 模块中使用 all 控制函数的导出

在functions中这样配置。这样就只能访问show方法而访问不了age方法

```py
__all__ = ["show"]

name = 'Lee'

def show():
    print(name)

def age():
    print(18)

print('versions is 1.0')
```

如下所示，使用age时就会报错。

```py
from Common.functions import *  # versions is 1.0
show() # Lee 
age() # 报错
```

但外部真的没有办法访问age了吗？其实也不是，只要使用这样的格式书写就又可以了

```py
from Common import functions # versions is 1.0
functions.age() # 18
```



