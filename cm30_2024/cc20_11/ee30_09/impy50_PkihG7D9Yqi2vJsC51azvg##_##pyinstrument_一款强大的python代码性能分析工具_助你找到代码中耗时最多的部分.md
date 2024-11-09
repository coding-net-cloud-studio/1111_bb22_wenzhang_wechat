[原文地址](https://mp.weixin.qq.com/s/PkihG7D9Yqi2vJsC51azvg)

# Pyinstrument:一款强大的 Python 代码性能分析工具,助你找到代码中耗时最多的部分


**原创** **小白这样学Python** [小白这样学Python](javascript:void(0);) *2024年11月09日 00:02* *湖南*

> Pyinstrument 是一款强大的 Python 代码性能分析工具,它能帮助你找到代码中耗时最多的部分,从而进行优化,提升程序执行效率.它就像一把探照灯,照亮了代码执行的黑暗角落,让你清晰地看到代码运行的真实情况.

![图片](attachments/640%5B13%5D.webp)

### 便捷的命令行使用

Pyinstrument 的使用非常简单,只需要在命令行中添加 `pyinstrument` 即可.例如,运行脚本 `script.py`:

```
pyinstrument script.py
```

Pyinstrument 会自动运行你的脚本,并在脚本结束后(或按下 `Ctrl+C` 时)输出一个彩色报告,展示代码执行时间在各个函数和模块中的分配情况.

### 丰富的选项参数

Pyinstrument 提供了一系列参数,可以定制报告内容和展现方式:

* • `-r RENDERER`:指定报告的渲染方式,支持 `text`,`html`,`json`,`speedscope` 等格式,以及自定义渲染器.
* • `-t`:渲染成时间线模式,保留调用顺序,不折叠重复调用.
* • `--hide`:隐藏指定路径的函数调用信息,例如 `--hide '*/lib/*'` 隐藏所有库函数的调用.
* • `--show`:显式展示指定路径的函数调用信息,即使被 `--hide` 隐藏.
* ![图片](attachments/640%5B14%5D.webp)

### 灵活的 Python API

除了命令行使用,Pyinstrument 还提供了丰富的 Python API,方便你将性能分析集成到你的代码中:

* • `with pyinstrument.profile():`:将代码块包裹在 `with` 语句中,即可对代码块进行性能分析.
* • `@pyinstrument.profile()`:用装饰器修饰函数或方法,方便快速进行性能分析.
* • `Profiler` 类:提供更灵活的接口,可以手动控制性能分析的启动,停止和输出.

### 强大的 Jupyter/IPython 支持

Pyinstrument 提供了 `%%pyinstrument` 魔法命令,方便在 Jupyter Notebook 或 IPython 环境中进行性能分析,可以分析单个代码行或代码块.

![图片](attachments/640%5B15%5D.webp)

### 集成到 Web 框架

Pyinstrument 可以方便地集成到各种 Web 框架中,对 Web 请求进行性能分析,帮助你发现 Web 应用中的瓶颈:

* • **Django:** 通过 `ProfilerMiddleware` 中间件和 `PYINSTRUMENT_PROFILE_DIR` 设置,可以自动对所有 Web 请求进行性能分析,并保存报告.
* • **Flask:** 使用 `before_request` 和 `after_request` 钩子函数,可以根据请求参数动态开启或关闭性能分析.
* • **FastAPI:** 可以编写一个异步中间件,根据请求参数开启或关闭性能分析.
* • **Falcon:** 可以编写一个中间件,在处理请求时开启性能分析,在处理响应时结束性能分析.
* • **Litestar:** 可以编写一个中间件,在处理请求时开启性能分析,并修改响应内容,返回性能分析报告.

### Pytest 测试性能分析

Pyinstrument 可以通过命令行参数 `-m pytest` 运行 pytest 测试框架,并生成整个测试套件的性能分析报告.也可以通过 `conftest.py` 中的 `fixture`,对单个测试函数进行性能分析.

### 总结

Pyinstrument 是一个功能强大,易于使用,灵活多样的 Python 代码性能分析工具,可以帮助你快速定位代码瓶颈,提升程序效率.无论是命令行使用,Python API,还是 Web 框架集成,Pyinstrument 都能满足你的不同需求.

项目地址:https://github.com/joerick/pyinstrument
