[原文地址](https://mp.weixin.qq.com/s/yCzIiZ2f50GI5VuDW_geAg)

项目地址：https://github.com/trekhleb/learn-python

# Learn-python:一个学习和使用Python的脚本集合,从入门到精通,代码示例,速查表,最佳实践一网打尽

**原创** **小白这样学Python** [小白这样学Python](javascript:void(0);) *2024年11月12日 00:02* *湖南*

> 还在为学习Python而苦恼吗?这个项目将带你轻松入门,并逐步掌握Python的精髓!`learn-python` 不仅是一个代码示例库,更是一个交互式的学习平台,让你在实践中快速提升编程技能.

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/VIupIhU5lf6JjJqpugQOicXsmoyNIORyKdGScqH1MmE2nT5jBnQrjoXoqBTDE895EULySmjVs5Zw0FB20R7ThMQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**项目简介**

`learn-python` 是一个按主题分类的 Python 脚本集合,包含丰富的代码示例,详细的解释,不同的用例以及扩展阅读链接.它既是一个"游乐场",又是一个"速查表",助你轻松玩转 Python.

**为什么称之为"游乐场"?**

你可以修改或添加代码,实时查看运行结果,并使用断言进行测试.你还可以使用代码检查工具,确保代码符合 Python 代码风格指南.这种交互式学习方式,可以让你更深入地理解代码,并从一开始就养成良好的编码习惯.

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/VIupIhU5lf6JjJqpugQOicXsmoyNIORyKHdOp5kr50hOrAfkceicPojlT1TYjGTWznWWicBLvrME5WhPbphk7meSg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**为什么称之为"速查表"?**

当你需要回顾 Python 语法或标准库用法时,可以随时查阅这些代码示例.由于代码中包含了大量的断言,你可以直接看到函数/语句的预期输出,无需运行代码.

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/VIupIhU5lf6JjJqpugQOicXsmoyNIORyKtONRZGXPxpc26IuXzZjZd6oG7lMeVmVO1ic6t2eRGNO6m5VfTsSOO3A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**如何使用这个宝库?**

每个 Python 脚本都遵循以下结构:

```
"""列表  <--- 主题名称

# @see: https://www.learnpython.org/en/Lists  <-- 扩展阅读链接

这里可能会有对当前主题的更详细的解释(例如,关于列表的一般信息).
"""


deftest_list_type():
"""子主题的解释在这里.

    每个文件都包含测试函数,用于说明子主题(例如,列表类型,列表方法).
    """

# 这是一个如何构建列表的示例.  <-- 注释解释了操作
    squares =[1,4,9,16,25]

# 列表可以被索引和切片.
# 索引返回项.
assert squares[0]==1# <-- 断言在这里说明了结果.
# 切片返回一个新列表.
assert squares[-3:]==[9,16,25]  # <-- 断言在这里说明了结果.
```

通常,你可以按照以下步骤学习:

1. 1. 找到你想要学习或回顾的主题.
2. 2. 阅读每个脚本文档字符串中的注释和/或链接的文档(如上例所示).
3. 3. 查看代码示例和断言,了解用法示例和预期输出.
4. 4. 更改代码或添加新的断言,看看它们是如何工作的.
5. 5. 运行测试和代码检查,确保代码正常工作并符合规范.

**涵盖的主题**

* •  **入门** :Python 简介,语法,变量,运算符
* •  **数据类型** :数字(包括布尔值),字符串,列表,元组,集合,字典,类型转换
* •  **控制流** :if 语句,for 语句,while 语句,try 语句,break 语句,continue 语句
* •  **函数** :函数定义,变量作用域,默认参数值,关键字参数,可变参数列表,参数解包,lambda 表达式,文档字符串,函数注解,函数装饰器
* •  **类** :类定义,类对象,实例对象,方法对象,类变量和实例变量,继承,多重继承
* •  **模块** :模块导入,包
* •  **错误和异常** :异常处理,引发异常
* •  **文件** :读写文件,文件对象的方法
* •  **附加内容** :pass 语句,生成器,标准库简介(序列化,文件通配符,字符串模式匹配,数学,日期和时间,数据压缩),用户输入

**如何运行代码**

**前提条件:** 安装 Python 3,推荐使用 `venv` 创建虚拟环境.

**安装依赖项:** `pip install -r requirements.txt`

**运行测试:** `pytest` 或 `pytest ./path/to/the/test_file.py` (运行特定测试)

**代码检查:** `pylint ./src/`

**总结**

这个项目提供了一个系统学习 Python 的绝佳途径,无论你是初学者还是有一定经验的开发者,都能从中受益匪浅.赶紧来体验吧!

**项目地址:https://github.com/trekhleb/learn-python**

#### cloudstudio中遇到的问题
```bash
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
autopep8 2.3.1 requires pycodestyle>=2.12.0, but you have pycodestyle 2.3.1 which is incompatible.

referencing 0.35.1 requires attrs>=22.2.0, but you have attrs 18.1.0 which is incompatible.
pylama 8.4.1 requires mccabe>=0.7.0, but you have mccabe 0.6.1 which is incompatible.
pylama 8.4.1 requires pycodestyle>=2.9.1, but you have pycodestyle 2.3.1 which is incompatible.
pylama 8.4.1 requires pyflakes>=2.5.0, but you have pyflakes 1.6.0 which is incompatible.
asttokens 2.4.1 requires six>=1.12.0, but you have six 1.11.0 which is incompatible.
jsonschema 4.23.0 requires attrs>=22.2.0, but you have attrs 18.1.0 which is incompatible.
trio 0.26.2 requires attrs>=23.2.0, but you have attrs 18.1.0 which is incompatible.
outcome 1.3.0.post0 requires attrs>=19.2.0, but you have attrs 18.1.0 which is incompatible.
```

#### 修订后的requirement
```bash
pycodestyle==2.12.0

mccabe==0.7.0
pyflakes
attrs==23.2.0

six==1.12.0

astroid==2.0.4
atomicwrites==1.1.5

flake8
isort==4.3.4
lazy-object-proxy==1.3.1

more-itertools==4.3.0
pluggy==0.7.1
py==1.5.4


pylint==2.1.1
pytest==3.7.2

wrapt==1.10.11


```