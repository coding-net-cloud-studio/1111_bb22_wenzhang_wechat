[原文地址](https://mp.weixin.qq.com/s/HNDN9nMW67cp9bznAJtgjQ)

**项目地址:** https://github.com/PyGithub/PyGithub


# PyGithub:一个用 Python 自动化掌控 GitHub 的利器

**原创** **小白这样学Python** [小白这样学Python](javascript:void(0);) *2024年11月09日 00:02* *湖南*

> PyGithub 是一个强大的 Python 库,用于与 GitHub API进行交互.它让开发者能够从 Python 脚本中管理 GitHub 资源,例如仓库,用户资料,组织等等.无论你是想自动化 GitHub 任务,构建 GitHub 应用程序,还是仅仅是想更方便地与 GitHub API 进行交互,PyGithub 都是你的理想选择.

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/VIupIhU5lf4nXIOn5WWqKJeWGaVkjC3QITz64CtFqgBVc4dVpEhcFqpXpIG77CL0AYQFnUBpLlib6RIgLIDZyUw/640?wx_fmt=jpeg&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

**PyGithub 的优势**

* • **简单易用:** PyGithub 提供了简洁直观的 API,让你能够轻松地访问 GitHub 资源,无需深入理解 GitHub API 的复杂细节.
* • **功能强大:** PyGithub 支持几乎所有 GitHub API v3 提供的功能,让你能够完成各种 GitHub 操作,例如创建仓库,创建问题,提交代码,管理团队等等.
* • **高效稳定:** PyGithub 是一个经过良好测试的库,拥有丰富的功能和稳定的性能,可以满足你的各种需求.
* • **活跃的社区:** PyGithub 拥有一个活跃的开发者社区,你可以随时获得帮助和支持.

**入门指南**

以下是如何使用 PyGithub 的简单示例:

1. 1. **安装 PyGithub**使用 pip 命令安装 PyGithub:

   ```
   pip install PyGithub
   ```
2. 2. **创建 GitHub 实例**首先,你需要创建一个 GitHub 实例:

   ```
   from github importGithub,Auth

   # 使用访问令牌进行身份验证
   auth =Auth.Token("your_access_token")

   # 连接到公共 GitHub
   g =Github(auth=auth)

   # 连接到 GitHub Enterprise
   g =Github(base_url="https://{hostname}/api/v3", auth=auth) 
   ```

   * • 访问令牌:你可以从你的 GitHub 账户设置页面获取个人访问令牌,并将其存储在 `your_access_token` 变量中.
   * • `base_url`:如果你使用的是 GitHub Enterprise,你需要设置 `base_url` 参数来指定你的 GitHub Enterprise 实例的地址.
3. 3. **访问 GitHub 资源**创建好 GitHub 实例后,你可以使用 `g` 对象访问各种 GitHub 资源.例如,以下代码获取当前用户的所有仓库:

   ```
   for repo in g.get_user().get_repos():
       print(repo.name)
   ```

   你也可以使用 PyGithub 的其他方法来操作 GitHub 资源,例如:

* • `g.get_repo("owner/repo_name")`:获取指定仓库
* • `g.get_user("username")`:获取指定用户
* • `g.get_organization("organization_name")`:获取指定组织

1. 4. **关闭连接**使用完 PyGithub 后,记得关闭连接:

   ```
   g.close()
   ```

**其他功能**

PyGithub 除了以上基本功能外,还支持许多其他功能,例如:

* •  **管理仓库** :创建仓库,修改仓库设置,添加协作者,管理分支,创建 Pull Request 等.
* •  **管理用户资料** :查看用户信息,修改用户资料,管理用户仓库等.
* •  **管理组织** :创建组织,修改组织设置,管理组织成员,管理组织仓库等.
* •  **管理问题** :创建问题,回复问题,标记问题,关闭问题等.
* •  **管理 Pull Request** :创建 Pull Request,合并 Pull Request,评论 Pull Request 等.
* •  **管理 Webhook** :创建 Webhook,管理 Webhook,删除 Webhook 等.

**开始使用 PyGithub**

PyGithub 为你提供了高效便捷的方式与 GitHub API 进行交互,轻松实现各种 GitHub 自动化操作.现在就尝试使用 PyGithub 探索 GitHub 的无限可能吧!

 **项目地址:** https://github.com/PyGithub/PyGithub
