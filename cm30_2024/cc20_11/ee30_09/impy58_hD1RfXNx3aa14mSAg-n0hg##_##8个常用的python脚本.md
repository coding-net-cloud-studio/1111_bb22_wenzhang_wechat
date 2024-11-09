[原文地址](https://mp.weixin.qq.com/s/hD1RfXNx3aa14mSAg-n0hg)
# 8个常用的 Python 脚本

**原创** **老邓** [印象Python](javascript:void(0);) *2024年11月04日 08:00* *陕西*

![](wmimages/300%5B1%5D.png)

**印象Python**提供一系列python技术文章.数据分析,网络爬虫,计算机底层文章等高质量技术文章!!

**85篇原创内容**

公众号

在 Python 编程中,有许多常用的脚本可以帮助我们进行文件操作,数据处理等任务.以下是一些常见的 Python 脚本示例,涵盖不同的应用场景.

## 1. 读取文本文件

### 读取文本文件的内容,并打印到控制台.

```
# 读取文本文件并打印内容
with open('example.txt', 'r', encoding='utf-8') as file:
    content = file.read()
    print(content)
```

```

```

适用于需要获取或查看文件内容的场景,例如日志分析或文档处理.

## 2. 写入文本文件

将数据写入文本文件.

```
# 将内容写入文本文件
with open('output.txt', 'w', encoding='utf-8') as file:
    file.write("Hello, World!\n")
    file.write("欢迎使用 Python!")
```

```

```

适合于生成报告,记录信息等操作.

## 3. CSV 文件读写

读取和写入 CSV 文件,常用于数据表格处理.

```
import csv

# 读取 CSV 文件
with open('data.csv', newline='', encoding='utf-8') as csvfile:
    reader = csv.reader(csvfile)
    for row in reader:
        print(row)

# 写入 CSV 文件
with open('output.csv', 'w', newline='', encoding='utf-8') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow(['Name', 'Age'])
    writer.writerow(['Alice', 25])
    writer.writerow(['Bob', 30])
```

```

```

广泛用于处理结构化数据,例如电子表格和数据库导出.

## 4. JSON 文件读写

读取和写入 JSON 格式的数据,适合存储复杂数据结构.

```
import json

# 写入 JSON 文件
data = {'name': 'Alice', 'age': 25}
with open('data.json', 'w', encoding='utf-8') as jsonfile:
    json.dump(data, jsonfile)

# 读取 JSON 文件
with open('data.json', 'r', encoding='utf-8') as jsonfile:
    data = json.load(jsonfile)
    print(data)
```

```

```

常用于 API 数据交互和配置文件管理.

## 5. 文件重命名和移动

重命名或移动文件到指定目录.

```
import os

# 移动和重命名文件
os.rename('old_name.txt', 'new_name.txt')
print("文件已重命名")

# 移动文件
os.replace('new_name.txt', '/new_directory/new_name.txt')
print("文件已移动")
```

```

```

适用于文件管理和整理的工作流程中.

## 6. 数据过滤与处理

对列表中的数据进行过滤和处理.

```
# 过滤偶数并将其平方
numbers = [1, 2, 3, 4, 5, 6]
squared_even = [x**2 for x in numbers if x % 2 == 0]
print(squared_even)  # 输出: [4, 16, 36]
```

```

```

可以用于数据清洗和预处理,例如从原始数据中提取特定信息.

## 7. 统计文本文件中的单词频率脚本功能

统计文本文件中每个单词出现的次数.

```
from collections import Counter
import re

# 统计单词频率
with open('example.txt', 'r', encoding='utf-8') as file:
    text = file.read().lower()  # 转为小写以避免重复
    words = re.findall(r'\w+', text)  # 提取单词
    word_count = Counter(words)
    print(word_count)
```

```

```

适合文本分析和信息检索,如博客文章或书籍的关键词分析.

## 8. 数据可视化

使用 Matplotlib 库绘制数据图形.

```
import matplotlib.pyplot as plt

```

```
# 数据准备
x = [1, 2, 3, 4, 5]
y = [2, 3, 5, 7, 11]

# 绘制图形
plt.plot(x, y, marker='o')
plt.title('Simple Line Plot')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.grid()
plt.show()
```

```

```

适合用于分析结果展示,比如展示销售趋势或实验数据.

以上就是八种常用的 Python 脚本示例.这些脚本能够帮助你在日常编程中高效地进行文件操作和数据处理.希望这些示例能够为你的 Python 学习之旅提供有价值的参考!
