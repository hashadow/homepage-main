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

https://hashadow.github.io/homepage-main-deploy/2025/06/28/article/image.png

