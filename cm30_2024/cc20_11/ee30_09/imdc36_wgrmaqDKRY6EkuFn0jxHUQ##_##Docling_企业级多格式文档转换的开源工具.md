[原文链接](https://mp.weixin.qq.com/s/wgrmaqDKRY6EkuFn0jxHUQ)
# Docling:企业级多格式文档转换的开源工具!

**原创** **JJJohn** [AGI Hunt](javascript:void(0);) *2024年11月07日 07:00* *北京*

![](attachments/300.png)

**AGI Hunt**关注AGI 的沿途风景!

**1043篇原创内容**

公众号

**一个多格式文档转换工具诞生了!**

![图片](attachments/640%5B28%5D.webp)

企业级RAG系统再添利器, **IBM最新开源的文档解析工具Docling** ,让PDF,Word,PPT等多种格式文档的处理变得如此简单.

这个名叫Docling的工具有什么过人之处呢?

## 超强的文档处理能力

作为一个企业级文档转换工具,Docling可不是一般的「格式转换器」.它能够:

* **支持多种格式** :PDF,DOCX,PPTX,图片,HTML等文档都不在话下
* **智能布局分析** :自动识别页面布局,阅读顺序和表格结构
* **OCR支持** :轻松处理扫描版PDF
* **统一输出** :将所有文档转换为标准的DoclingDocument格式

![图片](attachments/640%5B29%5D.webp)

## 为RAG而生的神器

Docling最厉害的地方在于它的 **RAG系统适配** .

它与LlamaIndex和LangChain无缝集成,让企业级RAG应用的文档处理不再是难题.你只需要几行代码就能完成文档的转换:

```

```

```
from docling.document_converter import DocumentConverter


source = "https://arxiv.org/pdf/2408.09869"  # document per local path or URL
converter = DocumentConverter()
result = converter.convert(source)
print(result.document.export_to_markdown())  # output: "## Docling Technical Report[...]"
```

<pre><strong><br/></strong></pre>

```
就这么简单,文档就被转换成了标准的Markdown和JSON格式!
```

<pre><p>完美适配各类大语言模型的输入需求<span>.</span></p></pre>

## 持续进化的野心

IBM的工程师们可不满足于此.他们已经在规划下一步的升级:

* **公式和代码提取**
* **元数据提取** :包括标题,作者,引用和语言
* **LangChain原生扩展**

这些功能的加入,将让Docling在文档处理领域变得更加强大.

![图片](attachments/640%5B30%5D.webp)

作为一个开源项目,Docling已经在GitHub上获得了6k 关注.它不仅支持macOS,Linux和Windows,还同时兼容x86_64和arm64架构.

**如果你正在为文档处理发愁,不妨试试这个来自IBM的开源利器.**

项目地址:https://github.com/DS4SD/docling

👇

👇

👇

👇

### 本文同步自知识星球<AGI Hunt>

星球实时采集和监控推特,油管,discord,电报等平台的热点AI 内容,并基于数个资讯处理的 AI agent 挑选,审核,翻译,总结到星球中.

* 每天约监控6000 条消息,可节省约800+ 小时的阅读成本;
* 每天挖掘出10+ 热门的/新的 github 开源 AI 项目;
* 每天转译,点评 10+ 热门 arxiv AI 前沿论文.

 **星球非免费.** 定价99元/年,0.27元/天.(每+100人,+20元.元老福利~)

* 一是运行有成本,我希望它能自我闭环,这样才能长期稳定运转;
* 二是对人的挑选,鱼龙混杂不是我想要的,希望找到关注和热爱 AI 的人.

**欢迎你的加入!**
