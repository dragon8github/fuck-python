### 值类型和引用类型

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

上demo中我们看到，girl并没有设置age的内容，但却因为boy的改变而改变了。这就是因为list是引用类型（可变变量）的原因导致的。所以要注意。那么怎么解决这个问题呢？只要将age放置在构造函数中定义、初始化即可，等同于创建一个新的对象

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



