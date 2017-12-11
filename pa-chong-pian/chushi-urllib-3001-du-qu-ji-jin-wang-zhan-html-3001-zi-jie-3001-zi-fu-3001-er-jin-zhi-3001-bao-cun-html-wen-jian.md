### urllib：内置的网络编程模块

> https://docs.python.org/3/library/urllib.html
>
> https://docs.python.org/3/library/urllib.request.html\#module-urllib.request

```py
from urllib import request

response =request.urlopen("http://fund.eastmoney.com/fund.html")
html=response.read()
print(html)

```



