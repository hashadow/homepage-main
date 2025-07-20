---
title: 修网页
date: 2025-07-04
layout: post
toc: true
excerpt: 个人主页的鸡毛蒜皮
---

目前有用的调整

1. 添加公式
2. 摘要显示
3. 添加图片
4. 增加栏目
5. 网页设置



## 公式

在主题icarus的config里面添加：

```yaml
math:
  enable: true
  engine: mathjax
```

然后在每一篇文章里面标明

```yaml
math: true
```



## 摘要

在每篇文章的yaml里面直接用:

```yaml
excerpt: 摘要内容
```



## 图片

### 对于post中的文章

先修改hexo渲染器为 hexo-renderer-markdown-it：

```bash
npm uninstall hexo-renderer-marked
npm install hexo-renderer-markdown-it --save
```

文件架构为：

```bash
source/_posts/
├── article.md
└── article/
    └── image.jpg
```

在md文档中markdown引用图片：

```markdown
![image](./image.jpg)
```

最终呈现网页路径为：

https://hashadow.github.io/homepage-main-deploy/2025/06/28/article/image.jpg

### 对于wiki中的文章

文件架构为：

```bash
source/wiki/physics_h_school
├── index.md
└── image.jpg
```

在md文档中markdown引用图片：

```markdown
![image](./image.jpg)
```

最终呈现网页路径为：

https://hashadow.github.io/homepage-main-deploy/wiki/physics/physics_h_school/image.jpg

## 栏目

在主题icarus的config里面找到menu并添加：

```yaml
navbar:
    menu:
        Home: /
        new_column: /column_filename # in source file
```

## 设置

```yaml
title: Hexo  # 网站主标题，显示在网页标题栏和首页等位置
subtitle: ''  # 网站副标题，可留空，也可显示在首页标题下
description: ''  # 网站描述，通常用于SEO
keywords: null  # 网站关键词，用于SEO，可填写为关键词列表
author: your name  # 网站作者名称，通常显示在文章作者处
language: zh-CN  # 网站语言，zh-CN代表简体中文
timezone: Asia/Shanghai  # 设置网站生成内容使用的时区

url: https://yourname.github.io  # 网站的根域名（用于生成绝对路径）
root: /homepage-main-deploy/  # 网站在服务器上的根目录（如果是子目录部署，要写上）

permalink: ':year/:month/:day/:title/'  # 文章永久链接的格式
permalink_defaults: null  # 设置永久链接中各项默认值（如未指定年、月等时的默认值）

pretty_urls:
  trailing_index: true  # 是否保留URL末尾的index.html
  trailing_html: true  # 是否保留URL末尾的.html

source_dir: source  # 源文件目录，Hexo 会从这里读取文章内容
public_dir: public  # 输出目录，Hexo 会将生成的静态网页放在这里

tag_dir: tags  # 标签页面目录
archive_dir: archives  # 归档页面目录
category_dir: categories  # 分类页面目录

code_dir: downloads/code  # 存放代码下载文件的目录

i18n_dir: ':lang'  # 多语言支持目录，用于国际化，:lang会被替换为语言标识

skip_render: null  # 设置哪些文件不被渲染（支持通配符），如设置为 ['README.md']

new_post_name: ':title.md'  # 新建文章的默认文件名格式，:title会被替换为文章标题

default_layout: post  # 默认使用的布局文件，如post/page等

titlecase: false  # 是否将标题转换为标题格式（每个单词首字母大写）

external_link:
  enable: true  # 是否开启外部链接新窗口打开
  field: site  # 应用于整站（site）或文章（post）
  exclude: ''  # 排除的链接，不应用此设置（如自己的域名）

filename_case: 0  # 文件名大小写设置（0: 不变，1: 小写，2: 大写）

render_drafts: false  # 是否渲染草稿（_drafts文件夹中的内容）

post_asset_folder: true  # 是否为每篇文章启用资源文件夹（与文章同名的文件夹）

relative_link: false  # 是否使用相对链接（否则使用绝对链接）

future: true  # 是否显示未来发布的文章（发布日期在当前时间之后）

syntax_highlighter: highlight.js  # 代码高亮工具，这里指定为highlight.js

highlight:  # highlight.js的相关设置
  line_number: true  # 是否显示代码行号
  auto_detect: false  # 是否自动检测语言
  tab_replace: ''  # 将tab替换为空格的数量（空表示不替换）
  wrap: true  # 是否给代码块包裹<pre><code>（true一般保留）
  hljs: false  # 是否启用highlight.js样式（与主题样式冲突时可设为false）

prismjs:  # prism.js设置（如使用它代替highlight.js）
  preprocess: true  # 是否在渲染前处理代码
  line_number: true  # 是否显示行号
  tab_replace: ''  # 同上，替换tab为多少空格

index_generator:
  path: ''  # 主页路径，默认为空表示根目录
  per_page: 10  # 每页显示的文章数量
  order_by: '-date'  # 排序方式（-date表示按日期倒序）

default_category: uncategorized  # 没有设置分类时默认的分类名

category_map: null  # 分类名称映射（如将“生活”统一改为“life”）

tag_map: null  # 标签名称映射（同上）

meta_generator: true  # 是否在<head>中生成Hexo版本号的meta标签（可关闭以提升安全性）

date_format: YYYY-MM-DD  # 文章日期显示格式
time_format: HH:mm:ss  # 文章时间显示格式

updated_option: mtime  # 使用文件修改时间作为文章更新时间，可设为mtime或date

per_page: 10  # 全站默认每页显示文章数量（分页）

pagination_dir: page  # 分页路径目录，如“page/2”就是第二页

include: null  # 设置在生成过程中强制包含的文件（通常为空）

exclude: null  # 设置在生成过程中排除的文件

ignore: null  # 忽略的文件或目录（不读取、不处理）

theme: icarus  # 使用的主题名称

```

