### python的装饰器

![](/assets/aasdas123123import.png)

我们玩魔兽争霸、Dota、王者农药、LOL的时候，如果英雄升级后乱加技能点或乱买装备，那么这个游戏还会好玩吗？ —— 我们总希望留着技能点，在游戏的过程中按需（个性化）分配：局势差的时候重生存，局势顺的时候重输出！

同样，在程序开发过程中，许多时候并不希望某个类 / 函数天生就非常庞大。一次性包含所有职能。那么我们就可以使用装饰者模式。可以随着需求和场景的变化。动态地给某个对象赋予一些额外的职能。

跟继承相比，装饰器是一种更轻便灵活的做法，这是一种“即用即付”的方式，比如天冷了就多穿一件外套，需要飞行时就在头上插一支竹蜻蜓，遇到一堆食尸鬼时就点开 AOE（范围攻击）技能。

---

### Example

```py
# 装饰器
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

### 带参数的装饰器

```py
# 装饰器
def Decorator(Doraemon):
    # 给哆啦A梦加入竹蜻蜓
    def surPerDoraemon(type):
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
newDoraemon('A')
newDoraemon('B')
newDoraemon('C')
```



