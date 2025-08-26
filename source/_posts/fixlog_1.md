---
title: 修网页
date: 2025-07-04
layout: post
toc: true
excerpt: 个人主页的鸡毛蒜皮
---

目前有用的调整

- [x] 添加公式
- [x] 摘要显示
- [x] 添加图片
- [x] 增加栏目
- [x] 网页设置
- [x] 任务格式渲染
- [ ] 任务复选框去点
- [x] 网页自动部署
- [x] 多端版本控制
- [ ] 内容折叠



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



## 任务复选框

### 渲染

安装 `markdown-it` 渲染器：

```bash
npm install hexo-renderer-markdown-it --save
npm install markdown-it-task-lists --save
```

在 Hexo 根目录下新建或修改 `_config.yml`（不是 theme/icarus 的配置，而是站点级别的 `config.yml`），加上：

```yaml
markdown:
  render:
    html: true
    xhtmlOut: false
    breaks: true
    linkify: true
    typographer: true
  plugins:
    - markdown-it-task-lists
```

**ToDo: 去掉复选框前的小点**



## 自动部署

### 目标

- 当你向 `homepage-main` 的主分支推送/合并代码时，自动：
  1. 安装依赖并渲染 Hexo
  2. 把 `public/` 推送到 `homepage-main-deploy`（可设为 `main` 或 `gh-pages` 分支）
  3. `homepage-main-deploy` 仓库开启 GitHub Pages 作为站点

### 准备工作（只做一次）

1. **Personal Access Token (PAT)**

   - 访问 GitHub → Settings → Developer settings → Personal access tokens (classic)
   - 新建一个 token，至少勾选 `repo` 权限
   - 复制 token，在源码库 `homepage-main` → Settings → Secrets and variables → Actions → **New repository secret**
   - 创建名为 **`GH_PAT`** 的 Secret，值粘贴你的 token

   > 说明：也可以用 Deploy Key + 写权限，但 PAT 更通用。

2. **配置 Pages（部署库）**

   - 在 `homepage-main-deploy` → Settings → Pages
   - Source 选择你要发布的分支（下面示例默认 `main`），目录选 `/ (root)`
   - 如果有自定义域名，添加 `CNAME`（见下方）。

3. **Hexo 主题（若为子模块）**

   - 如果 `themes/<your-theme>` 是 git submodule，请确保在源码库能正确拉取；否则在 CI 里要加 `submodules: true`。

### 在 `homepage-main` 新建工作流

在源码库里创建文件：`.github/workflows/deploy.yml`

```
name: Build & Deploy Hexo to homepage-main-deploy

on:
  push:
    branches: [ main ]   # 若你的默认分支不是 main，改成对应名称
  workflow_dispatch:      # 允许手动触发

permissions:
  contents: read

jobs:
  build-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source
        uses: actions/checkout@v4
        # with:
          # 若主题用了子模块，打开下面两行
          # submodules: true
          # persist-credentials: false

      - name: Use Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install deps
        run: |
          npm ci
          # 若未全局安装过 hexo-cli，也可以本地调用：npx hexo <cmd>
          npm i -g hexo-cli

      - name: Generate site
        run: |
          # 可选：清理
          npx hexo clean
          # 生成静态文件到 public/
          npx hexo generate

      # 如果需要写入 CNAME（自定义域名），在这里创建
      # - name: Add CNAME
      #   run: echo "example.com" > public/CNAME

      - name: Deploy to homepage-main-deploy
        run: |
          DEPLOY_REPO="github.com/hashadow/homepage-main-deploy.git"
          TARGET_BRANCH="gh-pages"  # 或 gh-pages

          cd public

          # 初始化独立仓库并推送
          git init
          git config user.name "${{ github.actor }}"
          git config user.email "${{ github.actor }}@users.noreply.github.com"
          git add .
          git commit -m "Deploy from ${GITHUB_REPOSITORY}@${GITHUB_SHA}"
          git branch -M ${TARGET_BRANCH}
          git push --force "https://${GH_PAT}@${DEPLOY_REPO}" ${TARGET_BRANCH}
        env:
          GH_PAT: ${{ secrets.GH_PAT }}
```

> 说明：
>
> - 这里直接用 `public/` 初始化一个临时 git 仓库，强推到部署库的目标分支（常用 `main` 或 `gh-pages`）。



## 多端版本控制

Mac: 先pull后push

Metion: 每两分钟自动pull和push



## 内容折叠 

not finish yet

by ChatGPT

明白了——你要的是**Markdown 标题（如 H2～H5）渲染成 HTML 后，标题下面整段内容能按层级折叠/展开**，而不是手动写 `<details>`。下面给你一套在 **Hexo + Icarus** 下可直接用的“自动折叠小标题内容”方案（不改主题源码，仅用 `inject` 注入 JS/CSS）。

### 一次性设置（推荐）

#### 1) 新建样式 `/source/css/collapsible.css`

```css
/* 折叠容器（默认收起） */
.hx-collapsible {
  overflow: hidden;
  transition: height 0.25s ease;
  height: 0;
}

/* 展开态 */
.hx-collapsible.open {
  height: auto;
}

/* 为了平滑过渡：先用具体高度过渡，再切换为 auto */
.hx-collapsible.animating {
  will-change: height;
}

/* 标题右侧的小按钮 */
.hx-toggle {
  margin-left: .5rem;
  font-size: .9em;
  cursor: pointer;
  user-select: none;
  opacity: .7;
}
.hx-toggle:hover {
  opacity: 1;
}

/* 让标题区域更像可交互，但不破坏原有 Anchor */
.hx-heading-wrap {
  display: flex;
  align-items: center;
  gap: .25rem;
}
.hx-heading-wrap .hx-title {
  flex: 1 1 auto;
}

/* 视觉指示符（▶/▼） */
.hx-toggle::before {
  content: "▶";
  display: inline-block;
  transform: translateY(-1px);
  transition: transform .2s ease;
}
.hx-toggle[aria-expanded="true"]::before {
  content: "▼";
  transform: translateY(-1px);
}

/* 可选：默认展开第一个 H2 小节（按需开启） */
/*
.hx-collapsible[data-level="2"]:first-of-type {
  height: auto;
}
.hx-toggle[data-level="2"]:first-of-type { aria-expanded: true; }
*/
```

#### 2) 新建脚本 `/source/js/collapsible.js`

```js
(function () {
  // 你要折叠哪些层级的标题：H2~H5（H1 一般是文章大标题，不折叠）
  const HEADING_MIN = 2;
  const HEADING_MAX = 5;

  // Icarus 有些站点启用 PJAX，需要在首次和 PJAX 完成后都运行
  function onReady(fn) {
    if (document.readyState === 'loading') {
      document.addEventListener('DOMContentLoaded', fn, { once: true });
    } else {
      fn();
    }
    // 兼容 Icarus 的 pjax
    document.addEventListener('pjax:complete', fn);
  }

  function isHeading(el) {
    if (!el || el.nodeType !== 1) return false;
    const m = el.tagName.match(/^H([1-6])$/);
    if (!m) return false;
    const level = parseInt(m[1], 10);
    return level >= HEADING_MIN && level <= HEADING_MAX;
  }

  function headingLevel(el) {
    return parseInt(el.tagName.replace('H', ''), 10);
  }

  function wrapHeadingWithToggle(h) {
    // 已经处理过就跳过
    if (h.dataset.hxProcessed === '1') return;

    // 把原标题文字包一个 span，旁边放一个 toggle
    const titleSpan = document.createElement('span');
    titleSpan.className = 'hx-title';
    while (h.firstChild) titleSpan.appendChild(h.firstChild);

    const toggle = document.createElement('button');
    toggle.className = 'hx-toggle';
    toggle.type = 'button';
    toggle.setAttribute('aria-expanded', 'false');
    toggle.setAttribute('aria-label', '展开/收起内容');
    toggle.dataset.level = String(headingLevel(h));

    const wrap = document.createElement('div');
    wrap.className = 'hx-heading-wrap';
    wrap.appendChild(titleSpan);
    wrap.appendChild(toggle);
    h.appendChild(wrap);

    h.dataset.hxProcessed = '1';
    return toggle;
  }

  function collectSectionContent(startHeading) {
    const myLevel = headingLevel(startHeading);
    const content = [];
    let el = startHeading.nextElementSibling;

    while (el) {
      if (isHeading(el)) {
        // 到达下一个“同级或更高层级”的标题 -> 结束
        if (headingLevel(el) <= myLevel) break;
      }
      content.push(el);
      el = el.nextElementSibling;
    }
    return content;
  }

  // 为了平滑高度动画：先固定高度，再过渡到 0/auto
  function setOpenState(box, open) {
    const setHeight = (h) => {
      box.style.height = `${h}px`;
      // 强制回流让浏览器识别起始高度
      // eslint-disable-next-line no-unused-expressions
      box.offsetHeight;
    };

    box.classList.add('animating');

    if (open) {
      // 从 0 -> 内容高度
      box.style.height = 'auto';
      const target = box.clientHeight;
      box.style.height = '0px';
      // 下一帧再设到目标高度
      requestAnimationFrame(() => {
        setHeight(target);
      });
    } else {
      // 从当前 auto -> 固定像素 -> 0
      const current = box.clientHeight;
      setHeight(current);
      requestAnimationFrame(() => {
        setHeight(0);
      });
    }

    const onEnd = () => {
      box.classList.remove('animating');
      if (open) {
        box.classList.add('open');
        box.style.height = 'auto';
      } else {
        box.classList.remove('open');
        box.style.height = '0px';
      }
      box.removeEventListener('transitionend', onEnd);
    };
    box.addEventListener('transitionend', onEnd, { once: true });
  }

  function applyCollapsibles(root) {
    // 在正文区域执行；Icarus 常见内容容器选择器如下，按你的站点结构选一个
    const containers = root ? [root] : document.querySelectorAll(
      '.article .article-inner, .post-block .post-body, .article-content, .markdown-body'
    );

    containers.forEach(container => {
      // 找到 H2~H5
      const headings = Array.from(container.querySelectorAll(
        Array.from({ length: HEADING_MAX - HEADING_MIN + 1 }, (_, i) => `h${i + HEADING_MIN}`).join(',')
      ));

      headings.forEach(h => {
        const toggle = wrapHeadingWithToggle(h);
        if (!toggle) return;

        // 收集本标题到“下一个同级或更高层级标题”之间的所有节点
        const sectionNodes = collectSectionContent(h);
        if (!sectionNodes.length) return; // 没内容就不包

        // 把这些节点包裹进折叠容器
        const box = document.createElement('div');
        box.className = 'hx-collapsible';
        box.dataset.level = String(headingLevel(h));

        // 默认：收起
        // 若你想某些层级默认展开，可在这里判断 level 决定加不加 open
        // if (headingLevel(h) === 2) box.classList.add('open'); // 例：默认展开所有 H2

        sectionNodes.forEach(n => box.appendChild(n));
        h.parentNode.insertBefore(box, h.nextSibling);

        // 点击按钮切换
        function toggleBox() {
          const isOpen = box.classList.contains('open');
          toggle.setAttribute('aria-expanded', String(!isOpen));
          setOpenState(box, !isOpen);
        }
        toggle.addEventListener('click', toggleBox);

        // 点击标题文字也可切换（避免影响标题内链接的点击）
        const titleSpan = h.querySelector('.hx-title');
        if (titleSpan) {
          titleSpan.addEventListener('click', (e) => {
            // 若点在内部链接上则放行
            if ((e.target instanceof Element) && e.target.closest('a')) return;
            toggle.click();
          });
        }
      });

      // 若 URL 带 #hash，自动展开对应标题所在段落
      if (location.hash) {
        const target = container.querySelector(location.hash);
        if (target && isHeading(target)) {
          const next = target.nextElementSibling;
          if (next && next.classList.contains('hx-collapsible')) {
            const btn = target.querySelector('.hx-toggle');
            if (btn) btn.setAttribute('aria-expanded', 'true');
            next.classList.add('open');
            next.style.height = 'auto';
          }
        }
      }
    });
  }

  onReady(() => applyCollapsibles());
})();
```

#### 3) 注入到站点（不改主题）

在站点根目录的 `_config.yml` 里用 `inject` 引入（你之前已用过这个方式）：

```yaml
inject:
  head:
    - <link rel="stylesheet" href="/css/collapsible.css">
  bottom:
    - <script src="/js/collapsible.js"></script>
```

然后：

```bash
hexo clean && hexo g && hexo s   # 本地预览
# 确认没问题再 hexo d 部署
```

### 使用 & 规则说明

- 该脚本会把 **H2～H5** 当作“可折叠标题”，并自动把**从该标题到下一个“同级或更高层级”标题之间的所有内容**打包成一个折叠块。
  - 例：H2 段落会一直包含到下一个 H2（或 H1）出现为止；其中的 H3/H4/H5 会被视为 H2 的子内容，一起被折叠。
- **默认全部收起**。
  - 想默认展开某些层级（比如 H2），在 JS 里找到注释 `// if (headingLevel(h) === 2) box.classList.add('open');` 取消注释即可。
- **标题右侧有“▶/▼”按钮**，点标题文字（非链接区域）也能切换。
- URL 若带 `#小标题锚点`，会**自动展开**该标题对应段落，方便分享直达。

#### 针对你给的示例怎么折叠

- 把你的内容按需要设置为 `##### 元素：`、`##### 课程结构：`、`##### 提问方法：`、`##### 符号`（H5），或者用 `##`/`###` 等。
- 构建后，H2～H5 的每个小节都会变成“点标题即可展开/收起”的折叠段落，**支持多层级嵌套**。

#### 常见坑位排查

- **资源路径**：`/css/…` 与 `/js/…` 要与 `_config.yml` 的 `root:` 保持一致（你之前的 `root: /homepage-main-deploy/`，那就写成 `/homepage-main-deploy/css/collapsible.css` 和 `/homepage-main-deploy/js/collapsible.js`）。
- **PJAX**：Icarus 若启用 PJAX，脚本里已监听 `pjax:complete`，无需额外处理。
- **CDN/缓存**：改了 JS/CSS 不生效，多半是缓存。先 `hexo clean`，浏览器强刷或关缓存再看。

------

如果你愿意，把你站点的 `root:`、是否启用 PJAX、文章正文容器的实际选择器（例如 `.article-content`）告诉我，我可以把选择器改到最稳妥的版本，并按你的 `root` 直接给出可粘贴的最终注入片段。
