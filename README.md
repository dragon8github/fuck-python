#### 安装pycharm

![](/assets/asdasdasdimport.png)

> [http://www.jetbrains.com/pycharm/?fromMenu](http://www.jetbrains.com/pycharm/?fromMenu)

| 组合键 | 功能 |
| :--- | :--- |
| CTRL + SHIFT + L | 格式化代码 |
| SHIFT \* 2 | Search Eventhing |

#### 官方文档

> [https://docs.python.org/3/library/functions.html?highlight=built](https://docs.python.org/3/library/functions.html?highlight=built)
>
> [https://docs.python.org/3/tutorial/index.html](https://docs.python.org/3/tutorial/index.html)

不管你学什么语言，都逃不出如下套路（部分）

1. 怎么定义变量、是否有数据类型、怎么在控制台输出？
2. 如何定义函数、如何定义类。面向对象的写法是如何的？
3. 如何调用外部类（或函数）？
4. 如何读写文件、网络编程？
5. 如何与数据库交互？
6. 如何和各种第三方库交互？
7. 是否有啥好的框架可以用？

### 内置函数库 Built-in Functions

> [https://docs.python.org/3/library/functions.html?highlight=built](https://docs.python.org/3/library/functions.html?highlight=built)

### 内置类型库 Built-in Constants

> [https://docs.python.org/3/library/constants.html](https://docs.python.org/3/library/constants.html)

### 内置模块库improved-modules

[https://docs.python.org/3/whatsnew/3.6.html\#improved-modules](https://docs.python.org/3/whatsnew/3.6.html#improved-modules)

---

### 小技巧

1、在cmd中使用python进入母体，但按下Ctrl + C 无法退出。需要手动使用exit\(\) 即可

![](/assets/135667import.png)

2、python中使用print打印时，如果遇到object和list等复杂类型时似乎不能完整打印出来。解决方案是强制转化为list类型。

```py
def isInt(item):
    return item.isdigit()

print(filter(isInt, 'ab123ef'))  # <filter object at 0x00535350>
print(list(filter(isInt, 'ab123ef'))) # 小技巧，使用强制转化为list可以输出内容：['1', '2', '3']
```

![](/assets/dssdadasadssdadasdasasimport.png)

3、lambda 表达式是洁癖程序媛的福音。通过它可以编写匿名函数。

```py
print(list(filter(lambda x: x.isdigit(), 'ab123ef'))) # ['1', '2', '3']
```



