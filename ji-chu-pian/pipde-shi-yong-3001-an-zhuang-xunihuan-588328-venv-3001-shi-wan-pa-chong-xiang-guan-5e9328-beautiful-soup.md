### pip的仓库地址

> [https://pypi.python.org/pypi](https://pypi.python.org/pypi)

---

### pip的安装和使用

![](/assets/asdaqweqweqweimport.png)

先检查你的python是否自带了pip

```bash
$ python -m pip help
```

![](/assets/124123import.png)

### （可选）手动安装pip

> [https://pypi.python.org/pypi/pip](https://pypi.python.org/pypi/pip)

解压pip-9.0.1.tar.gz，进入 pip-9.0.1目录下，打开命令行输入：

```bash
$ python setup.py install
```

再切换到 C:\Python27\Scripts 目录下输入：

```bash
$ ./easy_install pip
```

---

## 安装虚拟环境\(venv\)

我们先随便找一个地方创建一个文件夹，为了规范我在python根目录下新建venv文件夹，路径为C:\python\venv

接下来我们新建一个名为Lee的虚拟环境

```
$ python -m venv Lee
```

![](/assets/124245import.png)

接下来我们进入 Scripts 文件夹中，找到 activate.bat 文件夹并且执行它

```bash
$ cls

$ cd C:\python\venv\Lee\Scripts

$ activate.bat
```

![](/assets/1435324import.png)

这样我们就进入了虚拟环境：**C:\python\venv\Lee\Scripts**

---

### BeautifulSoup：使用pip安装著名的爬虫库

> BeautifulSoup 官方文档
>
> [https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)

先进入虚拟环境，然后使用如下命令安装

```
$ cd C:\python\venv\Lee\Scripts

$ python -m pip install beautifulsoup4
```

![](/assets/12341234234import.png)

安装完成后，我们可以在Lee虚拟环境中找到Lib\site-packages\bs4，就是我们刚刚安装的BeautifulSoup4了

![](/assets/13123123123import.png)

（ps：这时候我们在python根目录下的Lib是不存在bs4的，说明是完全隔离的一个环境）

---

### 使用BeautifulSoup

[https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/\#id10](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/#id10)

```py
from bs4 import BeautifulSoup

soup = BeautifulSoup("""
    <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title>Document</title>
        </head>
        <body>
            this is my html page
        </body>
    </html>
""", 'html.parser')

print(soup.html.head)
```

由于我们使用的是虚拟环境中的python.exe，所以运行的时候需要指定该环境下的python.exe

（ps：也可以先cd到虚拟目录下，然后执行python，因为会先从当前目录下查找，然后再去系统环境下查找）

> $ :/python/venv/Lee/Scripts/python.exe test.py
>
> &lt;head&gt;
>
> &lt;meta charset="utf-8"/&gt;
>
> &lt;title&gt;Document&lt;/title&gt;
>
> &lt;/head&gt;

---

### pychar 配置 虚拟环境下的python.exe来执行和解析

![](/assets/15123123123import.png)这样就可以解析了，如果不配置（使用默认的python解析）会报错说找不到bs4模块

![](/assets/3524625626import.png)

