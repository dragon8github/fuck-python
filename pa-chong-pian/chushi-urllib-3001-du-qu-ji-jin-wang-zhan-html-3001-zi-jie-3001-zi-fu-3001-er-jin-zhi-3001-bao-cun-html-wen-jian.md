### urllib：内置的网络编程模块

![](/assets/asdasdasdqweqweqweimport.png)

> [https://docs.python.org/3/library/urllib.html](https://docs.python.org/3/library/urllib.html)
>
> [https://docs.python.org/3/library/urllib.request.html\#module-urllib.request](https://docs.python.org/3/library/urllib.request.html#module-urllib.request)

```py
from urllib import request

response = request.urlopen("http://fund.eastmoney.com/fund.html")
html = response.read()
print(html)
```

根据老外的规定，如果是HTTP and HTTPS URLs，则会返回一个对象 http.client.HTTPResponse

进而我们要打开文档：[https://docs.python.org/3/library/http.client.html\#httpresponse-objects](https://www.gitbook.com/book/dragon8github/fuck-python/edit#)

---

### 字节和字符

1、计算机实际上只能存01010101010101\(二进制\)，一个数字就是一位（叫做bit），也是传输的最小单位；

2、每8位是一个字节（Byte）可代表一个字元\(A~Z\)、符号\(,.?!%&+-\*/\)、数字\(0~9\)；

3、网络传输单位、包括我们存在电脑中的文件等等，都是以字节的形式存储。然而对于一些纯文本的内容，可以把字节转化为字符让我们肉眼能识别出来。

**我们先创建一个htnls的文件，并且新建一个1.txt文件。**

```py
# -*- coding: utf-8 -*-
from urllib import request

response = request.urlopen("http://fund.eastmoney.com/fund.html")
# 由于页面是gb2312编码，所以需要先进行gb2312解码，但18030更加全面和强大。
html = response.read().decode('gb18030')

with open("./htmls/1.txt",'wb') as f:
    # 存储在文本中，还需要转化成文本通用编码格式，也就是utf8.不要问什么。
    f.write(html.encode('utf8'))
    f.close()
```



