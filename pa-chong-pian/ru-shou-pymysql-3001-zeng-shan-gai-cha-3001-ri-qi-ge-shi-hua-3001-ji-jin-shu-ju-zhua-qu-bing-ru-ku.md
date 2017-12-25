### 安装pymysql

[https://github.com/PyMySQL/PyMySQL](https://github.com/PyMySQL/PyMySQL)

这里我是使用虚拟环境来安装的，随意即可

```
$ cd C:\python\venv\Lee\Scripts
$ python -m pip install PyMySQL
```

![](/assets/12312315124import.png)

新建一个测试用的sql表

```php
SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for myfund
-- ----------------------------
DROP TABLE IF EXISTS `myfund`;
CREATE TABLE `myfund` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `fcode` varchar(255) DEFAULT NULL,
  `fname` varchar(255) DEFAULT NULL,
  `NAV` varchar(255) DEFAULT NULL,
  `ACCNAV` varchar(255) DEFAULT NULL,
  `updatetime` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=29 DEFAULT CHARSET=utf8;
```

---

### EXAMPLE

[https://github.com/PyMySQL/PyMySQL](https://github.com/PyMySQL/PyMySQL)

Common/config.py

```py
dbconfig = {
    'host': 'localhost',
    'port': 3306,
    'user': 'root',
    'password': 'root',
    'db': 'test',
    'charset': 'utf8'
}
```

index.php

```py
import pymysql
from pymysql.cursors import Cursor, SSCursor
from Common.config import dbconfig

result     =  [{'fcode': '167301', 'fname': '方正富邦保险主题指数分级', 'NAV': '1.3760', 'ACCNAV': '1.4410', 'updatetime': '2017-12-25 00:00:00'}]
connection = pymysql.connect(**dbconfig)
cursor     = Cursor(connection)

cursor.executemany('''
    INSERT INTO myfund(fcode, fname, NAV, ACCNAV, updatetime) 
    VALUES(%(fcode)s, %(fname)s, %(NAV)s, %(ACCNAV)s, %(updatetime)s)
    ON DUPLICATE KEY UPDATE `updatetime` = %(updatetime)s, `NAV` = %(NAV)s, `ACCNAV` = %(ACCNAV)s
''', result)
connection.commit()
connection.close()
```

### ![](/assets/15135234import.png)

### 坑爹记录

1、插入数据库的时候，请注意UTF-8的问题。也就是数据库和数据表都应该设置为UTF-8

```py
alter table <表名> convert to character set utf8 
```

2、py中的'''sql语句'''不要乱来。

