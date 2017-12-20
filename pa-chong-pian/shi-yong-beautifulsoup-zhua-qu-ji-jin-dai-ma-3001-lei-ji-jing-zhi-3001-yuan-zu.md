### 元组

和List很类似，且是不可变的。一旦你设定初始值后，不能修改

https://docs.python.org/3/library/stdtypes.html?highlight=tuple\#tuple

```py
# 定义一个空元组
result = ()

# 往元组中插入数据
# 一般我们会在里面塞比较灵活的数据类型 如list或dict
# 神坑：一定要在最后加入逗号（,）
result += ({"a":"1", "b":"2"},)
```

---

### 使用BeautifulSoup抓取基金代码

BeautifulSoup的 find 和 find\_all 方法

> [https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/\#find-all](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/#find-all)

这里我们使用上节课抓取的基金网站首页内容来解析

```py
# -*- coding: utf-8 -*-
from bs4 import BeautifulSoup

with open("./htmls/1.txt", 'rb') as f:
    html = f.read().decode('utf8')
    f.close()

soup = BeautifulSoup(html, "html.parser")
fCodes = soup.find("table", id="oTable").tbody.find_all("td", "bzdm")  # 基金编码
result = ()
for fCode in fCodes:
    result += ({"code": fCode.get_text()
                   , "name": fCode.next_sibling.find("a").get_text()
                   , "NAV": fCode.next_sibling.next_sibling.get_text()
                   , "ACCNAV": fCode.next_sibling.next_sibling.next_sibling.get_text()}
               ,)
print(result)
```



