### 安装SQLAlchemy

> [http://docs.sqlalchemy.org/en/latest/faq/connections.html](http://docs.sqlalchemy.org/en/latest/faq/connections.html)
>
> [http://docs.sqlalchemy.org/en/latest/intro.html\#installation](http://docs.sqlalchemy.org/en/latest/intro.html#installation)
>
> [http://docs.sqlalchemy.org/en/rel\_1\_1/](http://docs.sqlalchemy.org/en/rel_1_1/)
>
> [http://www.sqlalchemy.org/library.html\#buildingtheapp](http://www.sqlalchemy.org/library.html#buildingtheapp)

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

---

### 创建映射

1.1、新建 jt\_news 数据表

```php
SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for jt_news
-- ----------------------------
DROP TABLE IF EXISTS `jt_news`;
CREATE TABLE `jt_news` (
  `news_id` int(11) NOT NULL AUTO_INCREMENT,
  `news_title` varchar(50) DEFAULT NULL,
  `news_abstract` text,
  `news_updatetime` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `news_clicknum` int(11) DEFAULT NULL,
  `news_class` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`news_id`)
) ENGINE=MyISAM AUTO_INCREMENT=23 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of jt_news
-- ----------------------------
INSERT INTO `jt_news` VALUES ('2', 'Java开发新闻内容', 'Java新闻摘要', '2017-05-29 12:38:02', '11', '编程语言');
INSERT INTO `jt_news` VALUES ('3', 'PHP开发新闻', 'PHP新闻摘要', '2017-05-29 19:52:32', '13', 'web开发');
INSERT INTO `jt_news` VALUES ('4', 'js前后端分离开发网站项目的案例', 'javascript', '2017-05-28 19:55:59', '43', 'web开发');
INSERT INTO `jt_news` VALUES ('5', '开发中php和js结合的项目案例', '开发中php和js结合的项目案例摘要', '2017-06-04 13:59:14', '12', '实战开发');
```

1.2、新建映射文件mappers/info.py

注意 mappers 是一个包（Python Package），在 PyCharm 中 New -&gt; Python Package

```py
from sqlalchemy import Column, Integer, String, TEXT, TIMESTAMP
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class News(Base):
    __tablename__ = "jt_news"
    news_id = Column(Integer, primary_key=True, autoincrement=True)
    news_title = Column(String(50), nullable=False)
    news_abstract = Column(TEXT)
    news_updatetime = Column(TIMESTAMP)
    news_clicknum = Column(Integer, default=0)
```

1.3、index.py

```py
from sqlalchemy import create_engine, desc, text
from mappers.info import News
from sqlalchemy.orm import sessionmaker

# 添加echo=True参数可以打印出具体的sql语句。非常的友好和方便。
# engine = create_engine('mysql+pymysql://root:root@localhost/test?charset=utf8', echo=True)
engine = create_engine('mysql+pymysql://root:root@localhost/test?charset=utf8')
Session = sessionmaker(engine)
mysession = Session()

# 获取所有
result = mysession.query(News).all()
print(result[0].__dict__)

# 获取单条
result = mysession.query(News).first()
print(result.__dict__)
print(result.news_title)

# 过滤并且返回单个对象
result = mysession.query(News).filter_by(news_id=2).first()
print(result)

# 过滤并且返回列表
result = mysession.query(News).filter_by(news_id=2).all()
print(result)

# 过滤对象，注意使用的是==，效果同上
result = mysession.query(News).filter(News.news_id == 2).all()
print(result)

# limit + offset
result = mysession.query(News).filter(News.news_id > 2).limit(2).offset(0).all()
print(result)

# 排序orderby（正序）
result = mysession.query(News).filter(News.news_id > 2).order_by(News.news_id).limit(2).offset(0).all()
print(result)

# 排序orderby（倒序）
result = mysession.query(News).filter(News.news_id > 2).order_by(desc(News.news_id)).limit(2).offset(0).all()
print(result)

# 自定义过滤，其中:nid 和 :nclass 是占位符
result = mysession.query(News).filter(text("news_id > :nid and news_class= :nclass")).params(nid=2,nclass='web开发').all()
print(result)

# 根据主键id获取数据。但需要orm中设置主键才行。也就是primary_key=True
result=mysession.query(News).get(2)
print(result)

# 新增
news = News(news_title='测试新闻')
mysession.add(news)
mysession.commit()

# 修改
mysession.query(News).filter(News.news_id==2).update({"news_title":"测试修改标题"})
mysession.commit()
```

### Result

```js
C:\python\venv\Lee\Scripts\python.exe C:/Users/lizhaohong/PycharmProjects/mypro/test.py
{'news_title': 'Java开发新闻内容', 'news_id': 2, '_sa_instance_state': <sqlalchemy.orm.state.InstanceState object at 0x03634470>, 'news_clicknum': 11, 'news_updatetime': datetime.datetime(2017, 5, 29, 12, 38, 2), 'news_abstract': 'Java新闻摘要'}
{'news_title': 'Java开发新闻内容', 'news_id': 2, '_sa_instance_state': <sqlalchemy.orm.state.InstanceState object at 0x03634470>, 'news_clicknum': 11, 'news_updatetime': datetime.datetime(2017, 5, 29, 12, 38, 2), 'news_abstract': 'Java新闻摘要'}
Java开发新闻内容
<mappers.info.News object at 0x03634490>
[<mappers.info.News object at 0x03634490>]
[<mappers.info.News object at 0x03634490>]
[<mappers.info.News object at 0x03634870>, <mappers.info.News object at 0x036348D0>]
[<mappers.info.News object at 0x03634870>, <mappers.info.News object at 0x036348D0>]
[<mappers.info.News object at 0x03634BD0>, <mappers.info.News object at 0x036348D0>]
[<mappers.info.News object at 0x03634D10>, <mappers.info.News object at 0x036348D0>]
<mappers.info.News object at 0x03634E30>

Process finished with exit code 0
```



