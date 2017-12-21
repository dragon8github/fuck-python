### 安装pymysql

https://github.com/PyMySQL/PyMySQL

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
) ENGINE=MyISAM DEFAULT CHARSET=latin1;
```

---

简单的使用

https://github.com/PyMySQL/PyMySQL

```py
import pymysql
from pymysql.cursors import Cursor, SSCursor
from Common.config import dbconfig

result = ({'code': '167301', 'name': '方正富邦保险主题指数分级', 'NAV': '1.3760', 'ACCNAV': '1.4410'})
connection = pymysql.connect(**dbconfig)
cursor = Cursor(connection)
cursor.executemany("""
    insert into myfund(fcode, fname,NAV,ACCNAV,updatetime)
    values(%(fcode)s,%(fname)s,%(NAV)s,%(ACCNAV)s,%(updatetime)s)
    ON duplicate KEY UPDATE `updatetime`=%(updatetime)s,NAV=%(NAV)s,ACCNAV=%(ACCNAV)s
""", result)
connection.commit()
connection.close()
```



