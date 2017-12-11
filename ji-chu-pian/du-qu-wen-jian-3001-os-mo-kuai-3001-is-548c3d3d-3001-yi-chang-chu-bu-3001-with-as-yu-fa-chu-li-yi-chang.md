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

### 捕捉异常、None、is 、not

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



