### pip的仓库地址

> [https://pypi.python.org/pypi](https://pypi.python.org/pypi)

---

### pip的安装和使用

先检查你的python是否自带了pip

```bash
$ python -m pip help
```

![](/assets/124123import.png)

### 手动安装pip

> [https://pypi.python.org/pypi/pip](https://pypi.python.org/pypi/pip)

解压pip-9.0.1.tar.gz， 打开命令提示符 （开始--运行--cmd 命令， 回车） 进入 pip-9.0.1目录下输入：

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

```
$ cls

$ cd C:\python\venv\Lee\Scripts

$ activate.bat
```

![](/assets/1435324import.png)

这样我们就进入了虚拟环境

---

### BeautifulSoup：使用pip安装著名的爬虫库

> [https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)

先进入虚拟环境，然后使用如下命令安装

```
$ python -m pip install beautifulsoup4
```

![](/assets/12341234234import.png)

安装完成后，我们可以在Lee虚拟环境中找到Lib\site-packages\bs4，就是我们刚刚安装的BeautifulSoup4了

![](/assets/13123123123import.png)

（ps：这时候我们在python根目录下的Lib是不存在bs4的，说明是完全隔离的一个环境）

