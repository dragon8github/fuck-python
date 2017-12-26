### 安装SQLAlchemy

> [http://docs.sqlalchemy.org/en/latest/faq/connections.html](http://docs.sqlalchemy.org/en/latest/faq/connections.html)
>
> [http://docs.sqlalchemy.org/en/latest/intro.html\#installation](http://docs.sqlalchemy.org/en/latest/intro.html#installation)
>
> http://docs.sqlalchemy.org/en/rel\_1\_1/
>
> http://www.sqlalchemy.org/library.html\#buildingtheapp

这里我是使用虚拟环境来安装的，随意即可

```bash
$ cd C:\python\venv\Lee\Scripts
$ python -m pip install SQLAlchemy
```

---

### EXAMPLE

index.py

```py
from sqlalchemy import create_engine

engine = create_engine('mysql+pymysql://root:root@localhost/test?charset=utf8')

result = engine.execute('select * from myfund')
res = result.fetchall()
print(res)
```

![](/assets/IP0$F[$}8H4725DT44%28ZBDP.png)

