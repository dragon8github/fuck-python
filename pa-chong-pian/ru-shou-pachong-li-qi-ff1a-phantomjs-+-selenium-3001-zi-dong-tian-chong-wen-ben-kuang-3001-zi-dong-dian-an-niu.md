### phantomjs：无界面的浏览器内核

![](/assets/asdasd123123import.png)

phantomjs好比是一个无界面的浏览器内核，可以用它来执行脚本 。隐形的执行CSS选择、DOM操作等

官网地址：[http://phantomjs.org/download.html](http://phantomjs.org/download.html)

下载后，并把里面的 phantomjs.exe 拷贝出来。放到你喜欢的目录，譬如 C:\phantomjs.exe

然后设置环境变量，在PATH中加入这个地址即可。

![](/assets/asdasdzxc12import.png)

---

#### selenium

它是一个 web自动化测试框架，可以模拟一些人工操作，比如点击按钮、输入文本、填充表单等等

[http://seleniumhq.github.io/selenium/docs/api/py/](http://seleniumhq.github.io/selenium/docs/api/py/)

#### 安装

```bash
$ cd C:\python\venv\Lee\Scripts
$ python -m pip install selenium
```

根据老外的说明，它最终运行需要驱动（geckodriver）。可以使用官方告诉我们的chrome或firefox等，但是这些都不是我们想要的。我们需要的是刚刚我们创建的phantomjs。

```py
from selenium import webdriver
driver = webdriver.PhantomJS(executable_path=r'C:\PhantomJS.exe')
driver.get("https://www.baidu.com/")
searchBox=driver.find_element_by_id("kw")
searchBtn=driver.find_element_by_id("su")
searchBox.send_keys("jtthink.com")
searchBtn.click()
```

这里有一个神坑，必须制定PhantomJS.exe的路径才可以正常使用。

---



