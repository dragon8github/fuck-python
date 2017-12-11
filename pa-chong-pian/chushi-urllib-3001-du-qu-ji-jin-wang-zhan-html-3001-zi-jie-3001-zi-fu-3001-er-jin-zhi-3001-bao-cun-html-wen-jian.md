### urllib：内置的网络编程模块

> [https://docs.python.org/3/library/urllib.html](https://docs.python.org/3/library/urllib.html)
>
> [https://docs.python.org/3/library/urllib.request.html\#module-urllib.request](https://docs.python.org/3/library/urllib.request.html#module-urllib.request)

```py
from urllib import request

response =request.urlopen("http://fund.eastmoney.com/fund.html")
html=response.read()
print(html)
```

根据老外的规定，如果是HTTP and HTTPS URLs，则会返回一个对象 http.client.HTTPResponse

进而我们要打开如下文档

> https://docs.python.org/3/library/http.client.html\#httpresponse-objects

---

### 字节和字符

1、计算机实际上只能存0101010010101001\(二进制\).一个数字就是一位\(叫做bit\),也是传输的最小单位

2、每8位是一个字节\(Byte\)可代表一个字元\(A~Z\)、数字\(0~9\)、或符号\(,.?!%&+-\*/\)

3、网络传输单位、包括我们存在电脑中的文件等等都是以字节的形式存储。然而对于一些纯文本的内容，可以把字节转化为字符让我们肉眼能识别出来。

```py
from urllib import request

response =request.urlopen("http://fund.eastmoney.com/fund.html")
html = response.read()
with open("./htmls/1.txt",'wb') as f:
    f.write(html.decode('gb2312').encode('utf8'))
    f.close()
```



