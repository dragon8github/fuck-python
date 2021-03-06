### python的装饰器

![](/assets/aasdas123123import.png)

我们玩魔兽争霸、Dota、王者农药、LOL的时候，如果英雄升级后乱加技能点或乱买装备，那么这个游戏还会好玩吗？ —— 我们总希望留着技能点，在游戏的过程中按需（个性化）分配：局势差的时候重生存，局势顺的时候重输出！

同样，在程序开发过程中，许多时候并不希望某个类 / 函数天生就非常庞大。一次性包含所有职能。那么我们就可以使用**装饰器（Decorator）**。可以随着需求和场景的变化。动态地给某个对象赋予一些额外的职能。

跟继承相比，装饰器是一种更轻便灵活的做法，这是一种“即用即付”的方式，比如天冷了就多穿一件外套，需要飞行时就在头上插一支竹蜻蜓，遇到一堆食尸鬼时就点开 AOE（范围攻击）技能。

---

### Example

```py
# 哆啦A梦的装饰器
def Decorator(Doraemon):

    # 给哆啦A梦加入竹蜻蜓
    def surPerDoraemon():
        Doraemon()
        print("我拥有一个竹蜻蜓")

    # 返回一个超级哆啦A梦
    return surPerDoraemon

# 初级哆啦A梦
def Doraemon():
    print("我只是一只没有耳朵的机器猫")

# 通过装饰器给哆啦A梦添加功能
newDoraemon = Decorator(Doraemon)
newDoraemon()
```

### Result

![](/assets/imasdasd123123port.png)

---

### 带参数的装饰函数

**Example**

```py
# 哆啦A梦的装饰器
def Decorator(Doraemon):

    # 给哆啦A梦加入竹蜻蜓
    def surPerDoraemon(type = ''):
        Doraemon()

        if (type == 'A'):
            print("哆啦A梦使用了竹蜻蜓")

        elif (type == 'B'):
            print("哆啦A梦使用了时光机")

        else:
            print("哆啦A梦表示无能为力")

    # 返回一个超级哆啦A梦
    return surPerDoraemon


# 初级哆啦A梦
def Doraemon():
    print("我只是一只没有耳朵的机器猫")


# 通过装饰器给哆啦A梦添加功能
newDoraemon = Decorator(Doraemon)
newDoraemon()
newDoraemon('A')
newDoraemon('B')
```

**Result**

### ![](/assets/sdasd123123123import.png)

---

### @符号出现了

@是python中的一个装饰器语法糖，多说无益直接看代码。

**Example**

```py
# 哆啦A梦的装饰器
def FuckDecorator(Doraemon):

    # 给哆啦A梦加入竹蜻蜓
    def surPerDoraemon(type = ''):
        Doraemon()

        if (type == 'A'):
            print("哆啦A梦使用了竹蜻蜓")

        elif (type == 'B'):
            print("哆啦A梦使用了时光机")

        else:
            print("哆啦A梦表示无能为力")

    # 返回一个超级哆啦A梦
    return surPerDoraemon

# 通过@装饰器给哆啦A梦添加功能
@FuckDecorator
def Doraemon():
    print("我只是一只没有耳朵的机器猫")

Doraemon()
Doraemon('A')
Doraemon('B')
```

**result**

![](/assets/asdazxczxcimport.png)

---

### 带参数的装饰器 与 高阶函数

![](/assets/dsdghkkimport.png)

高阶函数是函数式编程的一个重要概念：指的是如果一个函数，接受一个函数作为参数，并且返回一个函数。那么这个函数就是高阶函数。高阶函数的做法和装饰器十分吻合。所以我们可以**带参数的装饰器**轻松实现高阶函数。

```py
# 哆啦A梦的装饰器
def Decorator(sex=''):

    # 男性哆啦A梦
    def BoyDoraemon(Doraemon):
        def surPerDoraemon():
            Doraemon()
            print("我叫哆啦A梦")

        return surPerDoraemon

    # 女性哆啦A梦
    def GirlDoraemon(Doraemon):
        def surPerDoraemon():
            Doraemon()
            print("我叫哆啦美")

        return surPerDoraemon

    # 根据装饰器的入参sex判断返回哪个类型
    if (sex.lower() == 'girl'):
        return GirlDoraemon
    else:
        return BoyDoraemon

@Decorator()
def Doraemon_no1():
    print("我只是一只没有耳朵的机器猫")

@Decorator(sex='Girl')
def Doraemon_no2():
    print("我只是一只保姆型机器猫")

Doraemon_no1()
Doraemon_no2()
```

![](/assets/的手段13123aimport.png)

---

### 把装饰器应用到类上

```py
def Decorator(func):
    # 1、由于我是装饰类方法，默认类方法的第一个参数是self（既类本身）。
    # 2、由于元组Tuple是无法删除第一个元素的，所以必须先使用list()转换为数组
    # 3、如果数组元素中存在数字，那么join是无法打印出来的。所以需要先使用(str(v) for v in args)将数组中所有的项都转化为string类型
    def showPower(*args):
        # 将元组转化为数组
        args = list(args)
        # 执行原始函数，并给他self（既类本身）
        func(args[0])
        # 删除第一个默认参数self（既类本身）。
        del args[0]
        print('我拥有：' + ','.join(str(v) for v in args))

    return showPower


class Doraemon:
    def __init__(self, **args):
        # 关键字参数是一个dict类型，必须使用get方法来获取
        self.name = args.get('name')

    @Decorator
    def sayHi(self):
        print("初次见面，我叫" + self.name)


doraemon = Doraemon(name='哆啦A梦')
doraemon.sayHi('竹蜻蜓', '时光机', '百宝袋')
```

![](/assets/asdsa123123123import.png)

---

### 内置的装饰器

staticmethod、classmethod和property，作用分别是把类中定义的实例方法变成静态方法、类方法和类属性

```py
class Doraemon:
    def __init__(self, **args):
        # 关键字参数是一个dict类型，必须使用get方法来获取
        self.name = args.get('name')

    @property
    def sayHi(self):
        return "初次见面，我叫" + self.name


doraemon = Doraemon(name='哆啦A梦')
print(doraemon.sayHi)
```

![](/assets/hjgjkhjkljklimport.png)

