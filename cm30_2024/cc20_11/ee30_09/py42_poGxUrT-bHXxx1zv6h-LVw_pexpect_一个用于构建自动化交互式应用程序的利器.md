# Pexpect：一个用于构建自动化交互式应用程序的利器

[原文地址](https://mp.weixin.qq.com/s/poGxUrT-bHXxx1zv6h-LVw)

**原创** **小白这样学Python** [小白这样学Python](javascript:void(0);) *2024年11月06日 00:02* *湖南*

> Pexpect 是一个强大的 Python 库，它使得 Python 在控制其他应用程序方面更加得心应手。Pexpect 的工作原理类似于 Don Libes 的 Expect，它允许你的脚本生成子应用程序并像人类输入命令一样控制它。

### **Pexpect 的核心功能**

Pexpect 的主要功能包括：

* • **生成子应用程序：** 使用 `pexpect.spawn()` 函数，你可以轻松地生成子应用程序，例如 ssh、ftp、passwd、telnet 等。
* • **控制子应用程序：** Pexpect 提供了多种方法来控制子应用程序，包括发送命令、读取输出、等待特定模式等。
* • **响应预期模式：** Pexpect 可以根据子应用程序输出中的特定模式做出反应，例如等待特定提示符或错误消息。

### **Pexpect 的应用场景**

Pexpect 在各种场景中都有广泛的应用，例如：

* • **自动化交互式应用程序：** 自动化登录服务器、执行命令、上传和下载文件等。
* • **自动化软件安装：** 在不同的服务器上重复执行软件安装脚本。
* • **自动化软件测试：** 模拟用户操作，测试软件功能和稳定性。

### **Pexpect 的优点**

* • **纯 Python 实现：** Pexpect 使用纯 Python 代码编写，易于安装和使用。
* • **跨平台支持：** Pexpect 在 Unix-like 系统和 Windows 上都可以使用。
* • **强大的功能：** Pexpect 提供了丰富的功能，可以满足各种自动化需求。
* • **易于学习：** Pexpect 的 API 简单易懂，学习曲线平缓。

### **Pexpect 的示例**

以下是一个简单的示例，展示如何使用 Pexpect 自动登录 SSH 服务器：

```
import pexpect

# 连接到 SSH 服务器
child = pexpect.spawn('ssh user@host')

# 等待提示符
child.expect('# ')

# 发送命令
child.sendline('ls -l')

# 等待命令输出
child.expect(pexpect.EOF)

# 打印输出
print(child.before)
```

在这个例子中，我们首先使用 `pexpect.spawn()` 函数生成一个 SSH 进程，然后使用 `expect()` 函数等待提示符 `# `。接下来，我们使用 `sendline()` 函数发送 `ls -l` 命令，并再次使用 `expect()` 函数等待命令输出。最后，我们使用 `before` 属性获取命令输出并打印出来。

### **安装 Pexpect**

使用 pip 安装 Pexpect：

```
pip install pexpect
```

### **总结**

Pexpect 是一个功能强大的 Python 模块，它可以帮助你自动化交互式应用程序，简化任务并提高效率。Pexpect 的跨平台支持和易用性使其成为自动化脚本的理想选择。

**项目地址：https://github.com/pexpect/pexpect**
