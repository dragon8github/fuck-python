### 值类型和引用类型

![](/assets/xvbgjgfhjfhimport.png)

String 类型在Python中被称为不可变类型，实际上就是值类型的意思

```py
class People:
    age = 19

    def __init__(self, inputName):
        self.name = inputName

    def info(self):
        print(self.name, self.age)

boy = People("Lee")
boy.age=21
boy.info() # Lee 21

girl = People("Mp")
girl.info() # Mp 19
```

上demo中我们看到，gril的age变量并不会因为boy的变化而变化，依然保留着19岁。这是理所当然的。那么接下来看看引用类型会如何？

什么是引用类型呢？list（列表、数组）就是一个引用类型，在python中被称为可变类型，可变类型就是保存着内存地址。意思就是说，如果你修改了一个变量，那么该变量所有内存相同的地址都会发生变化。具体表现如下

```py
class People:
    age = []

    def __init__(self, inputName):
        self.name = inputName

    def info(self):
        print(self.name, self.age)

boy = People("Lee")
boy.age.append(21)
boy.info() # Lee [21]

girl = People("Mp")
girl.info() # Mp [21]
```

上demo中我们看到，girl并没有设置age的内容，但却因为boy的改变而改变了。这就是因为list是引用类型（可变变量）的原因导致的。所以要注意。那么怎么解决这个问题呢？只要将age放置在构造函数中定义、初始化即可，等同于创建一个新的对象。

```py
class People:

    def __init__(self, inputName):
        self.name = inputName
        self.age = []

    def info(self):
        print(self.name, self.age)

boy = People("Lee")
boy.age.append(21)
boy.info() # Lee [21]

girl = People("Mp")
girl.info() # Mp []
```

主要看场景，如果一个变量希望被共享，那么应该被放置在外部。如果不是被共享，那么应该放置在构造函数中。

---

### 类的私有属性、方法

定义私有属性，在类中访问很正常，但在外部是无法正常访问了，除非通过非常特殊的语法。具体看下demo

```py
class People:

    __sex = '男'

    def __init__(self, inputName):
        self.name = inputName
        self.age = []

    def info(self):
        print(self.__sex)


boy = People("Lee")
boy.info() # 男
# print(boy.__sex) # 报错
print(boy._People__sex) # 男 
# 只有通过 类实例._类名__属性名/方法名 才可以访问
```

方法也是一样的道理，就不演示了

---

### 魔力函数的使用

获取注释内容，由于【'''】的注释方式可以换行，所以通常使用这个来做注解。可以实现类似java的注解。

```py
'''我是全局的注释'''

class Test:
    '''我是Test的注释'''
    pass

print(__doc__) # 我是全局的注释
print(Test.__doc__)# 我是Test的注释
```

获取函数名，通常可以判断当前函数是否为主函数（main），默认当前文件所在的模块，默认就是主函数main。

```py
class Test:
    pass

print(__name__)  # __main__
print(Test.__name__) # Test
```

获取类的详情信息

```py
class People:

    __sex = '男'

    def __init__(self, inputName):
        self.name = inputName
        self.age = []

print(People.__dict__)
# {'__module__': '__main__', '_People__sex': '男', 
# '__init__': <function People.__init__ at 0x000001BFF82DC158>, 
# '__dict__': <attribute '__dict__' of 'People' objects>, 
# '__weakref__': <attribute '__weakref__' of 'People' objects>, '__doc__': None}
```

---

### 字典类型，类似javascript中的对象

```py
me={"name":"Lee"}
user = dict(age=19, sex='nan')
print(me, user) # {'name': 'Lee'} {'age': 19, 'sex': 'nan'}

for key in user:
    print(key, user[key])
# age 19
# sex nan
```

这些方式都是定义字段的方式，非常简单和常用

