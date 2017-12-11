### 文件操作

> [https://docs.python.org/3/tutorial/inputoutput.html\#reading-and-writing-files](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)

```py
f=open("./files/test.txt")
print(f.read())
f.close()
```

![](/assets/23242import.png)

### OS模块

> [https://docs.python.org/3/library/os.html](https://docs.python.org/3/library/os.html)

常用的函数

* os.environ\['xxx'\]   获得系统环境变量
* os.getcwd 当前python脚本工作路径
* os.getpid\(\) 当前进程ID
* os.getppid\(\)  父进程ID \(3.2开始才有\)

```py
import os
print(__file__)
print(os.path.dirname(__file__))
print(os.path.dirname(os.path.dirname(__file__)))
```

![](/assets/12435345345345import.png)

### 捕捉异常、None、is语法 、not取反

> [https://docs.python.org/3/library/exceptions.html?highlight=exception](https://docs.python.org/3/library/exceptions.html?highlight=exception)

```py
import os

f = None
try:
    # 因为这个文件不存在
    f = open(os.path.dirname(__file__) + "/files/test.txt")
    print(f.read())
except:
    print("找不到这个文件")
finally:
    if f is not None:
        print('close')
        f.close()
```

---

### id\(\)

如果是普通数据类型（不可变数据类型、值类型）如String、Number、bool。他们的内存地址是不变的。  
但如果是列表（数组，可变类型，引用类型），他们的内存地址是动态的。  
举个例子

```py
a = 1
b = 1
print(id(a), id(b)) # 491411728 491411728

c = [1,2,3]
d = [1,2,3]
print(id(c), id(d)) # 5487032 5485232
```

### == 和 is的区别

```py
a = [1,2,3]
b = [1,2,3]
print(a==b)   # True
print(a is b) # False
```



