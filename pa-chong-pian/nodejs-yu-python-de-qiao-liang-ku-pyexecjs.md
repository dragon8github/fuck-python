### PyExecJS：Node.js 与 Python 的桥梁库

官网地址：[https://pypi.python.org/pypi/PyExecJS/](https://pypi.python.org/pypi/PyExecJS/)

github地址：[https://github.com/doloopwhile/PyExecJS](https://github.com/doloopwhile/PyExecJS)

#### PyExecJS 安装

```
$ cd C:\python\venv\Lee\Scripts
$ python -m pip install PyExecJS
```

#### EXAMPLE

前提是在本机上已经安装Nodejs环境了才有意义。

```py
import execjs
print(execjs.get().name) # Node.js (V8)

js_engine = execjs.get();
result = js_engine.eval("1+2")
print(result) # 3

js = """
    const str = "Hello";
    let getHello = name => str + ", " + name;
"""
compile = js_engine.compile(js)
result = compile.call('getHello', 'World')
print(result) # Hello, World
```

![](/assets/xzczxc54zx45cx54xcz54zcximport.png)

---



