# 目录
* [商企通前端博客](#商企通前端博客)
* [Hexo](#xexo)
* [如何使用](#如何使用)
* [具体写作](#具体写作)
* [如何共建](#如何共建)
* [hexo admin](#hexo admin)
* [注意](#注意)
* [todo](#todo)

# 商企通前端博客
https://sqt-fe.github.io/

构建工具：[hexo](https://hexo.io/zh-cn/)

使用的主题：[hexo-theme-hiker](https://github.com/iTimeTraveler/hexo-theme-hiker/blob/master/README.cn.md)

# Hexo
> hexo是一个博客框架

hexo文件夹结构
```
├── _config.yml 
├── db.json
├── node_modules 
├── package.json
├── public 
├── scaffolds 
├── source #所有文章文件放在这里
└── themes #主题文件夹
```

* _config.yml  站点的配置文件。
* db.json   缓存文件
* node_modules   安装的插件以及hexo所需的一些node.js模块。
* package.json  应用程序信息，配置hexo运行需要的js包。
* public  最终所见网页的所有内容
* scaffolds   模板文件夹。当新建一个文章时，会默认包含对应模板的内容。
* source  资源文件夹是存放用户资源的地方。所有的源文件都会被保存在_post文件夹中。除 posts 文件夹之外，开头命名为 (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。
* themes  存放主题文件，hexo会根据主题来生成静态页面。

# 如何使用

* 安装hexo
```bash
npm install -g hexo-cli
```

* 拉取仓库
```bash
git clone https://github.com/sqt-fe/sqt-fe.github.io.git
```

* 安装依赖
```bash
npm install
```
或
```bash
yarn
```

* 新建文章
```bash
hexo new "文章名"
```
> 文章名建议使用英文(是文件名称，与具体的文章标题有区别) ;创建的文件是md文件(使用markdow语法进行编写);生成的文件在`source/_posts`中

* 本地生成文章
```bash
hexo g
```
> 这里会将文章编译生成对应的html,js,css等文件，写入public文件夹中

* 本地效果预览
```bash
hexo s
```
> 方便本地调试查看效果

* 发布文章
```bash
hexo d
```
> 将编译出的public文件夹 上传至仓库，具体的配置见`_config.yml`文件中的`hexo`配置项；部署的时候一定要先执行`hexo g`命令,将静态文件生成

* 文件清理
```bash
hexo clean
```
> 这个命令会清理`hexo g`生成的文件

* 一键化命令
```bash
npm run dev
```
本地调试

```bash
npm run build
```
发布

# 具体写作
1. `hexo new "文件名"`成功后，你可以在`source/_posts`中找到你的 `md` 文件

2. 打开 `md` 文件，会发现头部的 文章 设置，类似
```
---
title: 第一篇测试文章
date: 2017-11-21 15:54:00
tags:
---
```
这里我们可以根据文章来具体设置
```
---
title: 第一篇测试文章
date: 2017-11-21 15:54:00
categories: 测试
tags: 第一篇文章
---
```
这样在网站上，你就可以在 `Categories` 和 `Tags` 栏目发现你的文章了。

3. 使用`hexo s` 命令 启动本地server ，用来预览你的文章效果

> 如果启动server后打开localhost:4000页面空白，可以尝试删除themes下的hiker文件夹，运行命令
`git clone https://github.com/sqt-fe/hexo-theme-hikers.git themes/hikers`，再重新启动服务试试

4. 使用`hexo clean`，清除public文件夹

5. 使用`hexo g` 将 `md` 编写的文章进行构建编译，生成对应的静态文件

6. 最后通过`hexo d` 将 静态文件发布至仓库，这样就大功告成！

# 如何共建

1. 博客样式共建

> 需要对`hexo`的文档熟悉
通过对`hexo-theme-hiker`的主题的修改，定制出自身的样式

2. 博客文章共建

小组成员通过使用`hexo`发布技术文章

# hexo admin

![](http://images.cnblogs.com/cnblogs_com/zqzjs/758380/o_WX20171124-122304@2x.png)

[hexo admin](https://jaredforsyth.com/hexo-admin/)让你爱上写作

运行命令`npm run write`,浏览器会自动打开`http://localhost:4000/admin`,开始你的写作把！

# 注意
文章中的图片建议使用 **图床**，可以选择[七牛云](https://www.qiniu.com/?hmsr=biaoti&hmpl=pinzhuan&hmcu=biaoti&hmkw=&hmci=)等

# Todo
* 博客样式、功能的优化
* 访问速度优化

