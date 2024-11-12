[原文地址](https://mp.weixin.qq.com/s/zYJU70P3jNvlVIXANnMALA)


# 群晖NAS搭建一款纯粹,干净的Markdown开源笔记软件

**原创** **老宁** [他们都叫我老宁](javascript:void(0);) *2024年03月25日 07:30* *云南*

## 项目地址

https://github.com/dullage/flatnotes

## 项目介绍

FlatNotes是一款纯粹,无干扰的笔记应用程序,没有数据库,专有格式,复杂的文件夹结构或类似的东西,让你只专注笔记内容本身

## 项目特性

* 干净简单的用户界面
* 响应式移动端界面
* 原生/所见即所得Markdown编辑模式
* 高级搜索功能
* 笔记"标签"功能
* 支持wikilink易链接其它笔记
* 明暗主题切换
* 多种认证选项
* 提供Restful API

## 安装部署

### Docker部署

```
docker run -d 
  -e "PUID=1000" 
  -e "PGID=1000" 
  -e "FLATNOTES_AUTH_TYPE=password" 
  -e "FLATNOTES_USERNAME=user" 
  -e "FLATNOTES_PASSWORD=changeMe!" 
  -e "FLATNOTES_SECRET_KEY=aLongRandomSeriesOfCharacters" 
  -v "$(pwd)/data:/data" 
  -p "8080:8080" 
  dullage/flatnotes:latest
```

### Docker Compose

```
version: '3'
services:
  flatnotes:
    image: dullage/flatnotes:latest
    container_name: flatnotes
    environment:
      - PUID=1000
      - PGID=1000
      - FLATNOTES_AUTH_TYPE=password
      - FLATNOTES_USERNAME=user
      - FLATNOTES_PASSWORD=changeMe!
      - FLATNOTES_SECRET_KEY=aLongRandomSeriesOfCharacters
    volumes:
      - ./data:/data
    ports:
      - "8080:8080"
    restart: unless-stopped
```

### 群晖部署

1. 登录群晖面板,打开Container Manager套件
2. 在注册表中搜索 `dullage/flatnotes`,下载最新版本的镜像

![图片](attachments/640%5B3%5D.webp)

3. 创建存放数据的文件夹(test/flatnotes)

![图片](attachments/640%5B4%5D.webp)

4. 设置文件夹权限为Everyone可读写

![图片](attachments/640%5B5%5D.webp)

5. 打开镜像界面,选择刚下载的flatnotes镜像,点击"运行"
6. 在创建容器时,设置端口转发,本地端口8080转发到容器的8080端口(如果冲突就设置别的本地端口)

![图片](attachments/640%5B6%5D.webp)

7. 新增存储空间设置,容器的/data映射到flatnotes群晖文件夹

![图片](attachments/640%5B7%5D.webp)

8. 增加环境变量如下图,用户名和密码可按需更改

![图片](attachments/640%5B8%5D.webp)

9. 确定设置后,启动容器即完成部署

## 效果预览

项目运行成功后,通过浏览器访问[http://你的设备IP:8080]flatnotes的前端界面,输入环境变量中的用户名和密码进行登录

![图片](attachments/640%5B9%5D.webp)

搜索所有笔记

![图片](attachments/640%5B10%5D.webp)

书写和预览模式

![图片](attachments/640%5B11%5D.webp)

## 我是老宁

一个热爱技术的程序员和极客,群晖NAS深度玩家!

专注NAS相关技术分享,原创!干货!

![图片](attachments/640%5B12%5D.webp)

觉得老宁的文章对你有帮助,记得 **点赞,收藏,加关注** !
