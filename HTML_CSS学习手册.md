# HTML & CSS 学习手册（详解版）

> 配套练习文件：`E:\website\demo.html`
> 版本：v2 · 2026-10-20
> 目标：两周内独立做出并上线一个个人网站。

---

## 怎么用这份文档

1. **第 0–6 章是 HTML，第 7–13 章是 CSS，第 15 章是实战。** 按顺序读。
2. **标签字典当参考书用。** 第 2–6 章每个标签都写了含义、默认表现、属性、示例、注意点。不用背，写代码时回来查。
3. **第 8 章（CSS 属性详解）、第 9 章（盒模型）、第 11 章（flex）是重点**，这三块决定你写出来的页面能不能看。
4. **每章末尾有「验收」。** 做不出来就回头重读。
5. **卡住超过 20 分钟再看答案。** 卡住本身就是学习过程的一部分。

---

## 阅读路线

**现在就要学的**（做第一版个人主页只需要这些）：

| 章节 | 内容 |
|---|---|
| 第 0–1 章 | 环境、F12、HTML 骨架 |
| 第 2 章 | 文本标签 |
| 第 3 章 | 列表与链接 |
| 第 4.1–4.2 | 图片和图注 |
| 第 6 章 | 语义结构 |
| 第 7–9 章 | CSS 基础、属性、盒模型 |
| 第 11 章 | flex |
| 第 15 章 | 实战 |

**暂时跳过**（收在[附录 D](#附录-d-暂缓内容用到再看)）：表格、表单、视频音频、iframe、svg。

**其他章节按需查**：第 10 章（`position` 只先看 `sticky`）、第 12 章（样式不生效时查）、第 13 章（要适配手机时看）、第 14 章（踩坑了对照）。

---

## 目录

**HTML 部分**

- [第 0 章 开始之前](#第-0-章-开始之前)
- [第 1 章 HTML 基础](#第-1-章-html-基础)
- [第 2 章 文本类标签](#第-2-章-文本类标签)
- [第 3 章 列表与链接](#第-3-章-列表与链接)
- [第 4 章 图片与多媒体](#第-4-章-图片与多媒体)
- [第 5 章 表格与表单](#第-5-章-表格与表单)
- [第 6 章 语义结构标签](#第-6-章-语义结构标签)

**CSS 部分**

- [第 7 章 CSS 基础](#第-7-章-css-基础)
- [第 8 章 常用属性详解](#第-8-章-常用属性详解)
- [第 9 章 盒模型（重点）](#第-9-章-盒模型重点)
- [第 10 章 display 与文档流](#第-10-章-display-与文档流)
- [第 11 章 flex 布局（重点）](#第-11-章-flex-布局重点)
- [第 12 章 层叠与优先级](#第-12-章-层叠与优先级)
- [第 13 章 响应式](#第-13-章-响应式)

**实战与附录**

- [第 14 章 二十个必须知道的坑](#第-14-章-二十个必须知道的坑)
- [第 15 章 实战：个人主页](#第-15-章-实战个人主页)
- [附录 A 速查表](#附录-a-速查表)
- [附录 B 标签索引 A–Z](#附录-b-标签索引-az)
- [附录 C 学习路线与上线](#附录-c-学习路线与上线)
- [附录 D 暂缓内容（用到再看）](#附录-d-暂缓内容用到再看)

---

## 第 0 章 开始之前

### 0.1 网站到底是什么

一个网站 = **一堆文件** + **一台把这些文件发给访客的机器**。

浏览器只做一件事：下载 HTML 文件，解析它，按里面的样式规则把内容画出来。

```
你在本地写文件 → 上传到服务器 → 用户访问域名 → 服务器发文件 → 浏览器渲染
```

**静态网站** = 没有后端逻辑，文件写好是什么就发什么。个人主页、博客、作品集、题解归档都是静态站。静态站可以免费托管（GitHub Pages / Cloudflare Pages），不用买服务器，不用备案。

### 0.2 三个文件的分工

| 文件 | 管什么 | 类比 |
|---|---|---|
| `.html` | 内容和结构 | 墙和房间 |
| `.css` | 外观和排版 | 装修、颜色、家具摆放 |
| `.js` | 交互和行为 | 开关、电梯、自动门 |

本手册只讲前两个。99% 的个人网站不需要写 JS。

### 0.3 建目录、建文件

```
E:\website\
├── index.html      ← 首页，文件名必须是 index
├── style.css       ← 样式表
├── demo.html       ← 练习场
└── HTML_CSS学习手册.md
```

`index.html` 是特殊文件名：服务器默认把它当作目录的首页。访问 `example.com/` 实际返回 `example.com/index.html`。

**创建文件的三种方式**：

- VS Code：打开文件夹 → 左侧空白处右键 → 新建文件 → 输入 `index.html`
- 资源管理器：右键 → 新建 → 文本文档 → 重命名（先勾选"显示文件扩展名"）
- PowerShell：`New-Item index.html`

### 0.4 开发者工具（F12）

这是你未来的主力工具，比任何教程都重要。

| 面板 | 用途 |
|---|---|
| **Elements** | 看页面结构，鼠标悬停能定位元素 |
| **Styles**（右侧） | 看该元素最终生效的所有 CSS，被划掉的是被覆盖的 |
| **盒模型图**（Styles 底部） | 直观显示 content / padding / border / margin 数值 |
| **Console** | 报错（比如图片 404） |
| **Network** | 看加载了哪些文件、哪个失败 |

**调试标准动作**：右键页面 → 检查 → 在 Elements 点中元素 → 右侧 Styles 直接改数值 → 页面实时变化 → 满意了把值抄回 CSS 文件。

### 0.5 让改动即时可见

- 最简单：改完 → `Ctrl+F5` 强制刷新（普通 F5 可能读缓存）
- 舒服一点：VS Code 装 **Live Server** 扩展 → 右键 HTML → Open with Live Server → 保存即刷新

---

## 第 1 章 HTML 基础

### 1.1 核心观念：HTML 描述"是什么"，不是"长什么样"

```html
<h1>大标题</h1>
<p>这是一段正文。</p>
```

`h1` 的意思是"这是一级标题"，`p` 的意思是"这是一个段落"。它们看起来一大一小，那是**浏览器默认样式**决定的，不是标签的含义。

理解这一点，你就不会问"怎么把 h2 调得比 h1 还大"——可以调，但你该先问自己标题层级是不是搞错了。

### 1.2 元素解剖

```html
<a href="https://codeforces.com" target="_blank">打开 Codeforces</a>
│  │                            │              │                │
│  │                            │              │                └─ 结束标签
│  │                            │              └─ 内容
│  │                            └─ 属性值
│  └─ 属性名
└─ 开始标签
```

四种成分：**标签名、属性、内容、结束标签**。

属性书写规则：

- 写在**开始标签**里，格式固定为 `名="值"`
- 值用双引号包起来（单引号也行，但别混）
- 多个属性用**空格**分隔，不是逗号
- 标签名不区分大小写，但**约定全小写**
- 属性名也全小写，多个单词用连字符：`data-user-id`

**空元素**（没有内容，也没有结束标签）：

```html
<img src="photo.jpg" alt="照片">
<br>
<hr>
<meta charset="UTF-8">
<input type="text">
<link rel="stylesheet" href="style.css">
```

### 1.3 全局属性（几乎所有标签都能用）

| 属性 | 作用 | 例子 |
|---|---|---|
| `id` | 页面内**唯一**标识，用于锚点跳转和 JS 定位 | `id="about"` |
| `class` | 类名，可多个，空格分隔，用于 CSS 选择 | `class="card card-wide"` |
| `style` | 行内样式，优先级很高，尽量别用 | `style="color:red"` |
| `title` | 鼠标悬停时的提示气泡 | `title="打开新窗口"` |
| `hidden` | 隐藏元素（等价 `display:none`） | `<p hidden>` |
| `lang` | 内容语言，影响读音和翻译 | `lang="zh-CN"` |
| `dir` | 文字方向 `ltr` / `rtl` | `dir="rtl"` |
| `tabindex` | Tab 键聚焦顺序 | `tabindex="0"` |
| `data-*` | 自定义数据，给自己的 JS 读 | `data-id="42"` |
| `contenteditable` | 让元素内容可编辑 | `contenteditable="true"` |

**`id` 和 `class` 的区别**：`id` 一页只能一个，`class` 可以重复用很多次。写 CSS 用 `class`，`id` 留给锚点跳转（`href="#about"`）和 JS。

### 1.4 文档骨架逐行解释

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>我的网站</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>你好</h1>
</body>
</html>
```

| 行 | 作用 | 不写会怎样 |
|---|---|---|
| `<!DOCTYPE html>` | 声明这是 HTML5 | 浏览器进怪异模式，盒模型计算规则变老版本 |
| `<html lang="zh-CN">` | 根元素，标注语言 | 屏幕阅读器读音错、翻译功能判断错 |
| `<head>` | 元信息容器，内容**不显示** | — |
| `<meta charset="UTF-8">` | 编码声明 | **中文全部乱码** |
| `<meta name="viewport" ...>` | 移动端视口 | 手机上页面被缩小成一小块 |
| `<title>` | 浏览器标签页文字 | 标签页显示文件名 |
| `<link rel="stylesheet">` | 引入外部 CSS | 没有样式 |
| `<body>` | 页面上能看见的一切 | — |

**判据**：`<head>` 里的东西全部不可见，`<body>` 里的东西才显示。

### 1.5 嵌套规则

```html
<div>
  <h1>标题</h1>
  <p>段落里有 <strong>加粗</strong> 文字。</p>
</div>
```

- 嵌套必须**正确闭合**：先开的后关（栈的顺序）
- 块级元素可以包含块级元素和行内元素
- 行内元素**不能**包含块级元素：`<span><div></div></span>` 是错的
- `<p>` 里不能放 `<div>`、`<h1>`、`<ul>`、`<table>`。浏览器不会报错，它会**强行把 `p` 闭合**，然后把 `div` 挤成兄弟节点——这是"布局莫名其妙错位"的常见原因

### 1.6 注释

```html
<!-- 这是注释，不会显示 -->
```

用途：给自己标段落、临时屏蔽代码。别写"这是标题"这种废话，写"改这里的颜色会同步影响导航栏"这种信息。

### 验收

做一个页面：正确骨架、UTF-8、标题、两段文字、一个链接。双击打开无乱码，F12 里能在 Elements 找到 `body`。

---

## 第 2 章 文本类标签

这一章每个标签都按 **含义 / 默认表现 / 属性 / 示例 / 注意** 来写。看的时候重点抓"含义"和"注意"，属性能用到再查。

### 2.1 标题 `<h1>` ~ `<h6>`

**含义** — 文档标题，`h1` 最高级，`h6` 最低级。表示**层级关系**，不是字号档位。

**默认表现** — 粗体，`h1` 约 2em（32px），逐级递减；上下有外边距；独占一行。

**属性** — 无专属属性，支持全局属性。

```html
<h1>杨渝渝</h1>
<h2>关于我</h2>
<h3>编程经历</h3>
```

**注意** —

- 一个页面通常只有**一个 `h1`**，就是页面主标题
- **不要跳级**：`h1` 下面直接 `h4` 会让文档大纲断裂
- 想要"看起来小一点的大标题"，改 CSS 的 `font-size`，不要换成 `h4`

**为什么重要** — 屏幕阅读器用户靠标题层级在页面里跳转，搜索引擎也用它判断结构。这是无障碍的基本要求。

### 2.2 段落 `<p>`

**含义** — 一段文字。语义上是一个完整的段落。

**默认表现** — 独占一行，上下各有约 1em 外边距（浏览器默认），左右无内边距。

**属性** — 无专属属性。

```html
<p>在练算法竞赛，日常刷 Codeforces。</p>
<p>这里会放题解和训练记录。</p>
```

**注意** —

- 每段一个 `<p>`，**不要用 `<br>` 制造段落间距**
- 不能包含块级元素（`div`、`ul`、`h1`、`table`），否则会被浏览器截断
- 想控制段落间距，用 CSS `margin`，别塞空的 `<p>&nbsp;</p>`

### 2.3 容器 `<div>` 和 `<span>`

**含义** — 通用容器，**没有任何语义**，纯粹为了分组以便加样式。`div` 是块级，`span` 是行内。

**默认表现** —

- `div`：`display: block`，独占一行，宽度撑满父元素，高度由内容决定
- `span`：`display: inline`，跟着文字流排，宽高无效

**属性** — 无专属属性。

```html
<div class="card">
  <h3 class="card-title">项目</h3>
  <p>描述里可以 <span class="highlight">强调</span> 某个词。</p>
</div>
```

**注意** —

- 有语义标签可用时优先用语义标签（见第 6 章）
- `span` 设 `width` / `height` 无效，要生效得改 `display: inline-block` 或 `block`
- 不要把 `div` 套到五六层只为居中，多半是布局方法不对

### 2.4 换行 `<br>` 与分割线 `<hr>`

**`<br>`**

**含义** — 在文字内部强制换行。空元素，无结束标签。

**默认表现** — 换行，不产生段落间距。

```html
<p>第一行<br>第二行</p>
```

**注意** — 只在**内容本身需要换行**时用，比如诗歌、地址、签名。控制布局间距一律用 CSS，不要堆 `<br><br><br>`——那是二十年前的做法，改起来是灾难。

**`<hr>`**

**含义** — 主题分隔线。语义上表示"话题转换"。

**默认表现** — 一条灰色横线，上下有外边距，独占一行。

```html
<p>上一节内容</p>
<hr>
<p>下一节内容</p>
```

**注意** — 如果只是想要一条装饰线，用 CSS 的 `border-bottom`，语义更准、样式更好控。

### 2.5 强调 `<strong>` / `<b>` / `<em>` / `<i>`

| 标签 | 含义 | 默认外观 | 要不要用 |
|---|---|---|---|
| `<strong>` | 内容**重要**，语气加重 | 加粗 | ✅ 推荐 |
| `<b>` | 只是"看起来粗"，无语义 | 加粗 | 少用 |
| `<em>` | 语气**强调**，重音 | 斜体 | ✅ 推荐 |
| `<i>` | 只是"看起来斜"，无语义 | 斜体 | 少用（图标字体除外） |

```html
<p><strong>注意：</strong>数据范围是 <em>n ≤ 10⁵</em>。</p>
```

**注意** — 视觉上一模一样，差别在屏幕阅读器。`<strong>` 会读成重音，`<b>` 不会。写内容就用语义版本；`<i>` 现在主要用来放图标（配合图标字体）。

### 2.6 其他行内文本标签

**`<u>` 下划线**

语义是"拼写错误或有特殊标注"，不是"链接样式"。链接别用 `u` 加下划线，用 CSS。

**`<s>` 删除线** / **`<del>` 删除内容**

```html
<p>原价 <s>¥99</s> 现价 ¥49</p>
<del datetime="2026-10-20">这句话已失效</del>
```

`s` 只是视觉删除线，`del` 表示"这段内容被删除了"（配合 `datetime` 记录时间）。

**`<small>` 小字**

```html
<p><small>最后更新：2026-10-20</small></p>
```

**`<mark>` 高亮**

```html
<p>搜索结果里 <mark>关键词</mark> 会被标黄。</p>
```

**`<code>` 代码** / **`<pre>` 预格式化**

```html
<p>用 <code>cout &lt;&lt; endl</code> 换行。</p>

<pre><code>int main() {
    return 0;
}</code></pre>
```

- `<code>` 行内代码，等宽字体
- `<pre>` 保留**所有空格和换行**，等宽字体
- 代码块用 `<pre><code>` 组合
- 注意 `<` 和 `>` 要写成 `&lt;` `&gt;`，否则会被当成标签

**`<kbd>` 键盘按键**

```html
<p>按 <kbd>Ctrl</kbd> + <kbd>F5</kbd> 强制刷新。</p>
```

**`<sub>` 下标 / `<sup>` 上标**

```html
<p>H<sub>2</sub>O，a<sup>2</sup> + b<sup>2</sup></p>
```

**`<abbr>` 缩写**

```html
<p><abbr title="Competitive Programming">CP</abbr> 选手</p>
```

鼠标悬停显示全称。对无障碍和 SEO 都有用。

**`<time>` 时间**

```html
<time datetime="2026-10-20">10 月 20 日</time>
```

`datetime` 给机器读（标准格式），标签间给人类读。

### 2.7 引用 `<blockquote>` / `<q>` / `<cite>`

**`<blockquote>`** — 块级引用，通常缩进显示。

```html
<blockquote cite="https://example.com/article">
  <p>引用的那段话。</p>
</blockquote>
```

**`<q>`** — 行内引用，浏览器会自动加引号。

```html
<p>他说 <q>先编译再运行</q>。</p>
```

**`<cite>`** — 引用来源的作品名（书名、文章名），默认斜体。

```html
<p>参考 <cite>算法导论</cite>。</p>
```

### 2.8 `<address>` 联系方式

**含义** — 与当前页面/文章相关的联系方式。

**默认表现** — 块级，斜体。

```html
<address>
  邮箱：<a href="mailto:me@example.com">me@example.com</a>
</address>
```

**注意** — 只用于**联系方式**，不要拿它包裹任意地址文本。

### 2.9 实体字符（转义）

HTML 里 `<`、`>`、`&` 有特殊含义，要显示它们本身必须转义：

| 写法 | 显示 |
|---|---|
| `&lt;` | `<` |
| `&gt;` | `>` |
| `&amp;` | `&` |
| `&quot;` | `"` |
| `&nbsp;` | 不换行空格 |
| `&copy;` | © |
| `&times;` | × |
| `&rarr;` | → |

**注意** — `&nbsp;` 不要拿来当缩进或制造间距，那是排版手段，不是空格。

### 验收

做一个"自我介绍"页面，包含：`h1` + 两三个 `h2`、若干 `p`、至少一处 `strong`/`em`、一段 `<pre><code>` 代码块、一个 `<time>`。要求标题层级正确（不跳级），F12 里看结构是嵌套合理的一棵树。

---

## 第 3 章 列表与链接

### 3.1 无序列表 `<ul>` + `<li>`

**含义** — 顺序**不重要**的项目集合。`ul` = unordered list，`li` = list item。

**默认表现** — `ul` 上下有外边距、左侧有缩进（约 40px）；`li` 前面有圆点 `•`。

**属性** — 无专属属性（老式 `type="square"` 已废弃，用 CSS `list-style-type`）。

```html
<ul>
  <li>图论</li>
  <li>数据结构</li>
  <li>数论</li>
</ul>
```

**注意** —

- `ul` 的**直接子元素只能是 `li`**，不能塞 `div`、`p`
- 要嵌套列表，套在 `li` **里面**：

```html
<ul>
  <li>编程
    <ul>
      <li>C++</li>
      <li>Python</li>
    </ul>
  </li>
</ul>
```

**常见用途** — 导航菜单（配合 CSS 去掉圆点）、特性清单、目录。

### 3.2 有序列表 `<ol>` + `<li>`

**含义** — 顺序**重要**的项目集合。会自动编号。

**属性** —

| 属性 | 作用 | 例子 |
|---|---|---|
| `type` | 编号样式，`1` `a` `A` `i` `I` | `type="a"` |
| `start` | 从第几号开始 | `start="3"` |
| `reversed` | 倒序编号 | `reversed` |

```html
<ol start="3">
  <li>编译</li>
  <li>运行</li>
</ol>
```

**注意** — 步骤、排名、排行榜用 `ol`；"有哪些项"用 `ul`。

### 3.3 定义列表 `<dl>` / `<dt>` / `<dd>`

**含义** — 术语与解释的配对。`dl` = description list，`dt` = term（术语），`dd` = description（描述）。

**默认表现** — `dd` 有左缩进，`dt` 与 `dd` 交替排列。

```html
<dl>
  <dt>AC</dt>
  <dd>Accepted，通过。</dd>
  <dt>WA</dt>
  <dd>Wrong Answer，答案错误。</dd>
</dl>
```

**注意** — 适合术语表、FAQ、键值对展示。一个 `dt` 可以配多个 `dd`。

### 3.4 链接 `<a>`

**含义** — 超链接，指向另一个资源（页面、文件、位置、邮件地址）。

**默认表现** — 蓝色带下划线，访问过变紫色，悬停时指针变手形。

**属性** —

| 属性 | 作用 | 说明 |
|---|---|---|
| `href` | **目标地址**，必填 | 没有 `href` 就不是链接 |
| `target` | 打开位置 | `_blank` 新标签页，`_self` 当前页（默认） |
| `rel` | 与目标的关系 | `noopener` `noreferrer` `nofollow` |
| `download` | 下载而不是打开 | `download="文件名"` |
| `title` | 悬停提示 | — |

**五种常见写法**：

```html
<!-- 1. 外部网站 -->
<a href="https://codeforces.com" target="_blank" rel="noopener">Codeforces</a>

<!-- 2. 站内页面 -->
<a href="about.html">关于我</a>

<!-- 3. 页内锚点：跳到 id="projects" 的元素 -->
<a href="#projects">跳到项目</a>

<!-- 4. 邮件 / 电话 -->
<a href="mailto:me@example.com">发邮件</a>
<a href="tel:+8613800000000">打电话</a>

<!-- 5. 下载文件 -->
<a href="notes.pdf" download="算法笔记.pdf">下载笔记</a>
```

**注意** —

- `target="_blank"` **必须**配 `rel="noopener"`，否则新页面能通过 `window.opener` 操纵你的原页面（安全问题）
- 链接文字要有意义。写"点这里"对屏幕阅读器用户是灾难，写"查看项目"
- 锚点跳转要求目标元素有对应的 `id`，且 `id` 唯一
- 站内跳转用**相对路径**，不要写死 `http://localhost`

### 3.5 导航 `<nav>`

见第 6 章语义标签，这里先记住结构：

```html
<nav>
  <ul>
    <li><a href="#about">关于</a></li>
    <li><a href="#works">项目</a></li>
  </ul>
</nav>
```

配合 CSS 去掉圆点：

```css
nav ul { list-style: none; padding: 0; margin: 0; display: flex; gap: 16px; }
```

### 验收

做一个"练过的算法"列表：嵌套两层（大类 + 子项），并用 CSS 去掉圆点改成横向排列。再加一个导航条，三个锚点链接本篇三个区块，点击能跳过去。

---

## 第 4 章 图片与多媒体

### 4.1 图片 `<img>`

**含义** — 嵌入一张图片。空元素，没有结束标签。

**默认表现** — 行内元素，按图片原始尺寸显示，底部有几像素空隙（因为是行内元素，按基线对齐）。

**属性** —

| 属性 | 作用 | 是否必填 |
|---|---|---|
| `src` | 图片路径或 URL | ✅ 必填 |
| `alt` | 替代文本（加载失败/读屏时显示） | ✅ 强烈建议 |
| `width` / `height` | 宽高（纯数字，不带 px） | 建议 |
| `loading` | `lazy` 懒加载 / `eager` 立即 | 可选 |
| `decoding` | `async` 异步解码 | 可选 |
| `srcset` / `sizes` | 响应式多分辨率 | 进阶 |

```html
<img src="avatar.jpg" alt="我的头像" width="200" loading="lazy">
```

**注意** —

- `alt` **不是可选的**。图片挂了显示它，读屏读它，搜索靠它理解内容。写"我的头像"而不是"图片1"
- 写 `width`/`height` 可以避免图片加载时页面跳动
- 图片下面那条空隙是行内元素基线造成的，全局加 `img { display: block }` 消掉：

```css
img { max-width: 100%; height: auto; display: block; }
```

这三行建议放进全局样式：图片永远不超出容器，宽高比不变。

- 装饰性图片用 `alt=""`（空字符串），告诉读屏"跳过它"

### 4.2 图注 `<figure>` + `<figcaption>`

**含义** — `figure` 是"独立的内容单元"，通常是图、代码、图表；`figcaption` 是它的说明文字。

```html
<figure>
  <img src="chart.png" alt="训练量统计">
  <figcaption>图 1：近三个月的训练量</figcaption>
</figure>
```

**注意** — 当图片需要一个说明时用 `figure` 包起来，语义上"图 + 说明"是一个整体。不是每张图都要 `figure`。

### 4.3 视频 / 音频 / iframe / svg（暂缓）

⏸ 第一版个人主页不需要放视频、不需要嵌别人的页面、也不需要画矢量图。内容见[附录 D](#附录-d-暂缓内容用到再看)。

### 验收

做一个图片区块：一张 `img`（带 `alt`、`width`、`loading="lazy"`），用 `figure` 包起来加 `figcaption`。然后把 `src` 改成一个不存在的路径，看 `alt` 文字是否正确显示出来。。

---

## 第 5 章 表格与表单（暂缓）

⏸ **这两样你现在的个人主页都用不到。** 静态站没有后端，表单提交没有接收方；表格只用于展示表格型数据，个人主页暂时也没有。

完整内容收在[附录 D](#附录-d-暂缓内容用到再看)，等真要用了再回来看。

---

## 第 6 章 语义结构标签

### 6.1 为什么不全部用 div

```html
<div class="header">
  <div class="nav">...</div>
</div>
<div class="main">
  <div class="article">...</div>
</div>
```

能跑，样式也能写。但有三个问题：

1. **半年后你自己看不懂**：`div class="box2"` 是什么？
2. **屏幕阅读器无法导航**：视障用户靠语义标签在区块间跳转
3. **搜索引擎无法理解结构**：不知道哪块是正文

语义标签在**视觉上完全等价于 `div`**，样式一个不少一个不多。差别只在信息。

### 6.2 `<header>`

**含义** — 一个区块的**页眉**：标题、logo、导航等引导性内容。

```html
<header class="site-header">
  <h1>杨渝渝</h1>
  <p>算法竞赛选手</p>
  <nav>...</nav>
</header>
```

**注意** — 不一定是整页的页头。一篇文章里也可以有自己的 `<header>`（放标题和日期）。

### 6.3 `<nav>`

**含义** — 主要**导航链接**的集合。

```html
<nav>
  <ul>
    <li><a href="#about">关于</a></li>
    <li><a href="#works">项目</a></li>
  </ul>
</nav>
```

**注意** — 只用于**主要导航**。页脚那种零散的几个链接不需要包 `nav`。一页可以有多个 `nav`，建议加 `aria-label` 区分（如 `aria-label="主导航"`）。

### 6.4 `<main>`

**含义** — 页面**主体内容**，与页面主题直接相关、且在全站各页之间不重复的内容。

```html
<main>
  <section>...</section>
</main>
```

**注意** — 一个页面**只能有一个 `<main>`**，且不能嵌套在 `header`/`footer`/`nav` 里面。

### 6.5 `<article>` 和 `<section>`（最容易混）

**`<article>`**

**含义** — 一段**独立完整**的内容。判断标准：**把它单独抽出来放到别处，仍然讲得通、仍然有意义**。

典型：一篇博客文章、一个新闻条目、一个论坛帖子、一张商品卡。

**`<section>`**

**含义** — 有**主题**的内容分节，通常**带自己的标题**。

典型：文章里的"背景"、"方法"、"结果"三节。

**判断流程**：

```
这块内容能单独拿出去发布吗？
├─ 能 → <article>
└─ 不能
    ├─ 它有主题、需要标题来概括吗？
    │   ├─ 有 → <section>
    │   └─ 没有 → <div>
```

```html
<main>
  <article>
    <h2>第一次 CF 上分记录</h2>
    <p>正文...</p>
    <section>
      <h3>赛前准备</h3>
      <p>...</p>
    </section>
    <section>
      <h3>比赛过程</h3>
      <p>...</p>
    </section>
  </article>
</main>
```

**注意** — 别滥用。如果一个 "section" 没有标题、纯粹为了套样式，那就是 `div`。

### 6.6 `<aside>`

**含义** — 与主内容**间接相关**的补充内容：侧栏、作者简介、相关链接、广告。

```html
<aside>
  <h3>关于作者</h3>
  <p>在读，刷题中。</p>
</aside>
```

**注意** — 去掉 `aside` 不影响主内容的完整性。

### 6.7 `<footer>`

**含义** — 区块的页脚：版权、联系方式、相关链接、作者信息。

```html
<footer>
  <p>© 2026 杨渝渝</p>
</footer>
```

**注意** — 和 `header` 一样，可以是整页的，也可以是 `article` 内部的（放标签、作者、时间）。

### 6.8 `<details>` + `<summary>`

**含义** — 可展开/收起的折叠块，**不需要 JS**。

```html
<details>
  <summary>这道题怎么做？</summary>
  <p>先跑最短路，再在 DAG 上 DP。</p>
</details>
```

- `<summary>` 是**始终可见**的标题行
- 其余内容默认折叠
- 加 `open` 属性默认展开：`<details open>`

**用途** — FAQ、题解折叠、长内容折叠。个人站很好用。

### 6.9 完整页面结构范本

```html
<body>
  <header class="site-header">
    <h1>站点名</h1>
    <nav aria-label="主导航">
      <ul>
        <li><a href="#about">关于</a></li>
        <li><a href="#works">项目</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="about">
      <h2>关于</h2>
      <p>...</p>
    </section>

    <section id="works">
      <h2>项目</h2>
      <article class="card">
        <h3>项目一</h3>
        <p>...</p>
      </article>
      <article class="card">
        <h3>项目二</h3>
        <p>...</p>
      </article>
    </section>
  </main>

  <aside>
    <h3>相关</h3>
    <ul><li><a href="...">链接</a></li></ul>
  </aside>

  <footer>
    <p>© 2026</p>
  </footer>
</body>
```

### 验收

把第 2 章做的自我介绍页重构成这个结构：`header` + `nav` + `main` + 两个 `section` + `footer`。视觉上应该**完全没有变化**——如果变了，说明你写错位置了。

---

## 第 7 章 CSS 基础

### 7.1 三种引入方式

```html
<!-- 1. 行内样式：优先级最高，最难维护，只在 JS 动态改样式时用 -->
<p style="color: red">红字</p>

<!-- 2. 内部样式表：单页练习可以，多页会重复 -->
<style>
  p { color: red; }
</style>

<!-- 3. 外部样式表：正式项目唯一正确做法 -->
<link rel="stylesheet" href="style.css">
```

外部样式表的好处：**一个文件管所有页面**，改一次全站生效。做多页站时用行内样式意味着要改 5 个文件。

### 7.2 语法

```css
选择器 {
  属性: 值;
  属性: 值;
}
```

```css
h1 {
  color: #2563eb;
  font-size: 28px;
  margin-bottom: 8px;
}
```

三条硬规则：

1. **属性名和值之间是冒号，每条声明后是分号**。漏分号会导致后面所有声明失效
2. 分号可以省略最后一条，但**永远写上**，加属性时才不会忘
3. 注释是 `/* ... */`，不能用 `//`

### 7.3 选择器全表

| 选择器 | 写法 | 含义 | 权重 |
|---|---|---|---|
| 标签 | `p` | 所有 `p` 元素 | 1 |
| 类 | `.card` | `class="card"` 的所有元素 | 10 |
| ID | `#main` | `id="main"` 的那一个元素 | 100 |
| 群组 | `h1, h2` | 同时选中多个 | 各自算 |
| 后代 | `.card p` | `.card` 里**任意层级**的 `p` | 相加 |
| 子元素 | `.card > p` | `.card` 的**直接子** `p` | 相加 |
| 相邻兄弟 | `h1 + p` | 紧跟 `h1` 后的第一个 `p` | 相加 |
| 通用兄弟 | `h1 ~ p` | `h1` 后面所有同级 `p` | 相加 |
| 属性 | `a[target="_blank"]` | 带该属性的元素 | 10 |
| 伪类 | `a:hover` | 某种状态 | 10 |
| 伪元素 | `p::first-line` | 元素的某个部分 | 1 |
| 通配 | `*` | 所有元素 | 0 |

**常用伪类**：

| 伪类 | 触发时机 |
|---|---|
| `:hover` | 鼠标悬停 |
| `:focus` | 获得焦点（输入框点进去、Tab 键选中） |
| `:active` | 按下瞬间 |
| `:visited` | 链接访问过 |
| `:first-child` | 是父元素的第一个子元素 |
| `:last-child` | 是最后一个子元素 |
| `:nth-child(n)` | 第 n 个（`2n` 偶数，`odd` 奇数） |
| `:not(.x)` | 除 `.x` 之外 |

**常用伪元素**：

```css
p::first-line { }                    /* 第一行 */
p::before     { content: "→ "; }     /* 元素前面插入内容 */
p::after      { content: ""; }       /* 元素后面插入内容 */
```

**日常就用类选择器。** 一个元素可以有多个类，空格分隔：

```html
<div class="card card-wide">...</div>
```

```css
.card      { padding: 16px; }
.card-wide { width: 100%; }
```

这是 CSS 最重要的复用手段。类名取**语义名**（`.card`、`.nav`、`.post-title`），不要取外观名（`.red-box`、`.big-text`）——外观会变，名字不会。

### 7.4 CSS 变量

```css
:root {
  --main: #2563eb;
  --text: #1f2937;
  --bg: #f8fafc;
  --radius: 10px;
}

h1    { color: var(--main); }
.card { border-radius: var(--radius); background: var(--bg); }
```

`:root` 是文档根元素，这里定义的变量**全站可用**。改配色只改三行，不用满文件搜索替换。新手也建议一开始就用。

变量可以带备用值：`color: var(--main, #2563eb);`（变量没定义时用后面的）。

---

## 第 8 章 常用属性详解

每个属性按 **作用 / 取值 / 例子 / 坑** 写。查的时候先看"作用"和"取值"。

### 8.1 颜色

**`color`** — 文字颜色。**`background-color`** — 背景色。

**写法四种**：

```css
color: red;                    /* 关键字，约 140 个内置名，不精细 */
color: #2563eb;                /* 十六进制，最常用 */
color: rgb(37, 99, 235);       /* 三通道 0-255 */
color: rgba(37, 99, 235, 0.5); /* 带透明度，0 全透明 1 不透明 */
color: hsl(220, 80%, 53%);     /* 色相 0-360，饱和度，亮度 */
```

**十六进制速记**：`#RRGGBB`，两两一组分别是红绿蓝。`#fff` 白色（每两位相同可压缩成一位），`#000` 黑色，`#2563eb` 蓝色。

**坑** — `color` 会**继承**给子元素，`background-color` 不会。给 `body` 设 `color` 全站文字都变，设背景色只影响 `body` 本身。

### 8.2 背景

```css
background-color: #f8fafc;

background-image: url(bg.jpg);
background-repeat: no-repeat;      /* repeat(默认) / repeat-x / repeat-y / no-repeat */
background-position: center;       /* left top / center / 百分比 / 像素 */
background-size: cover;            /* cover 铺满裁切 / contain 完整显示 / 100% auto */
background-attachment: fixed;      /* 滚动时背景不动 */

/* 简写，顺序随意 */
background: #f8fafc url(bg.jpg) center / cover no-repeat fixed;
```

**渐变也属于 background**：

```css
background: linear-gradient(180deg, #eef2ff 0%, #f8fafc 100%);
background: linear-gradient(90deg, #2563eb, #7c3aed);
```

`linear-gradient(角度, 颜色 位置, 颜色 位置)`。`0deg` 向上，`90deg` 向右，`180deg` 向下。

**坑** — `background-size` 必须写在图片之后；简写时用 `/` 分隔 `position` 和 `size`。

### 8.3 字体

**`font-family`** — 字体族，可写多个，浏览器**从左往右找第一个存在的**。

```css
font-family: system-ui, -apple-system, "Segoe UI", "Microsoft YaHei", sans-serif;
```

最后一个应该总是通用族（`sans-serif` 无衬线 / `serif` 衬线 / `monospace` 等宽）。字体名有空格要加引号。

**`font-size`** — 字号。

```css
font-size: 16px;      /* 固定 */
font-size: 1rem;      /* 相对根字号（浏览器默认 16px）→ 16px */
font-size: 1.5rem;    /* → 24px */
font-size: clamp(24px, 5vw, 40px);  /* 响应式 */
```

**`font-weight`** — 字重。

```css
font-weight: 400;  /* normal，正文 */
font-weight: 700;  /* bold，粗体 */
font-weight: 300;  /* light，需要字体本身支持 */
```

**`font-style`** — `normal` / `italic` 斜体。

**`line-height`** — 行高，决定行与行的距离。

```css
line-height: 1.8;   /* 无单位 = 字号的倍数，推荐 */
line-height: 28px;  /* 绝对值，不推荐 */
```

**无单位最好**：随字号自动缩放，子元素继承时也正确。正文 1.6–1.8，标题 1.2–1.4。

**`letter-spacing`** — 字间距。`0.5px` 或 `0.02em`。标题加一点点显精致，正文别加。

**坑** — 中英文混排时，中文字体要往后放，让英文优先用英文字体，否则英文也用中文字体渲染，很难看。

### 8.4 文本

**`text-align`** — 水平对齐。`left`（默认）/ `right` / `center` / `justify`。

作用于**行内内容**（文字、`inline` 元素、`inline-block`），不是块级盒子本身。

**`text-decoration`** — 装饰线。

```css
text-decoration: none;             /* 去掉链接下划线 */
text-decoration: underline;
text-decoration: line-through;
text-decoration: underline dotted #2563eb;  /* 样式 + 颜色 */
```

**`text-transform`** — `uppercase` / `lowercase` / `capitalize`。只影响显示，不改内容。

**`text-indent`** — 首行缩进。`text-indent: 2em;` 中文段落首行缩进两字。

**`white-space`** — 空白和换行怎么处理。

```css
white-space: normal;   /* 默认，合并空格，自动换行 */
white-space: nowrap;   /* 不换行，会溢出 */
white-space: pre;      /* 保留空格和换行，像 <pre> */
```

**`text-overflow`** — 溢出时怎么显示，必须配 `overflow: hidden` 和 `white-space: nowrap`：

```css
.ellipsis {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;   /* 超出部分显示 … */
}
```

### 8.5 尺寸

```css
width: 320px;        /* 固定宽度 */
width: 50%;          /* 相对父元素 */
width: 100%;         /* 铺满父元素 */
max-width: 720px;    /* 最大不超过，小屏自动缩小 —— 布局最常用 */
min-height: 100vh;   /* 至少一屏高 */
height: auto;        /* 由内容决定（默认） */
```

**`max-width` 比 `width` 好用**：写 `width: 720px` 在小屏会溢出，写 `max-width: 720px` 会自动缩小。

### 8.6 盒模型四件套

```css
margin: 0 auto;              /* 块级元素水平居中（要有宽度） */
padding: 16px 20px;          /* 上下 16，左右 20 */
border: 1px solid #e5e7eb;   /* 宽度 样式 颜色 */
border-radius: 8px;          /* 圆角 */
border-radius: 50%;          /* 圆形（元素本身是正方形时） */
```

详见第 9 章。

### 8.7 阴影

```css
box-shadow: 水平偏移 垂直偏移 模糊半径 扩展半径 颜色;
box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);   /* 常用卡片阴影 */
box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);  /* 悬停加深 */
```

可以写多层，用逗号分隔。

**坑** — 别用纯黑 `rgba(0,0,0,0.5)`，会发灰发脏。用 `0.05`–`0.12` 的低透明度。

### 8.8 透明度与可见性

```css
opacity: 0.6;         /* 0 全透明，1 不透明。整个元素含子元素一起变 */
visibility: hidden;   /* 隐藏但占位置 */
display: none;        /* 隐藏且不占位置 */
```

### 8.9 溢出

```css
overflow: visible;   /* 默认，超出部分照样显示 */
overflow: hidden;    /* 裁掉超出部分 */
overflow: auto;      /* 需要时出现滚动条 */
overflow: scroll;    /* 总是显示滚动条 */
overflow-x: auto;    /* 只控制横向，宽表格常用 */
```

### 8.10 列表样式

```css
list-style: none;              /* 去掉前面的圆点/数字 */
list-style-type: disc | circle | square | decimal | lower-alpha;
list-style-position: inside;   /* 标记放在内容内部 */
```

去掉默认缩进还要清 padding：

```css
ul { list-style: none; margin: 0; padding: 0; }
```

### 8.11 过渡与变换

**`transition`** — 属性变化时的动画。

```css
transition: 属性 时长 缓动 延迟;
transition: all 0.2s ease;
transition: color 0.2s ease, transform 0.3s ease;  /* 多个用逗号 */
```

写在**元素本身**上（不是 `:hover` 里），这样进场退场都有动画。

**`transform`** — 变形，不影响布局。

```css
transform: translateY(-2px);   /* 上移 2px */
transform: scale(1.05);        /* 放大 5% */
transform: rotate(45deg);      /* 旋转 */
transform: translateX(10px) scale(1.1);  /* 可组合，空格分隔 */
```

**常用组合（卡片悬停）**：

```css
.card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
}
```

### 8.12 光标

```css
cursor: pointer;      /* 手形，可点击的东西都用 */
cursor: default;      /* 箭头 */
cursor: text;         /* 文字输入 */
cursor: not-allowed;  /* 禁用 */
```

### 8.13 层级 `z-index`

`z-index` 只在元素有定位（`position` 不为 `static`）或处于 flex/grid 子项时生效。数字越大越靠上。

---

## 第 9 章 盒模型（重点）

### 9.1 四层结构

页面上**每一个元素都是一个矩形盒子**，从里到外四层：

```
┌─────────────────────────────────┐
│        margin（外边距）          │  ← 盒子之间的间隔，透明，不计入尺寸
│  ┌───────────────────────────┐  │
│  │    border（边框）          │  │  ← 可见的边
│  │  ┌─────────────────────┐  │  │
│  │  │  padding（内边距）    │  │  │  ← 内容到边框的距离
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │   content      │  │  │  │  ← 文字/图片本身
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

四边分别控制的简写，顺序是**上右下左**：

```css
.box {
  margin: 10px;                 /* 四边都是 10 */
  margin: 10px 20px;            /* 上下 10，左右 20 */
  margin: 10px 20px 30px;       /* 上 10，左右 20，下 30 */
  margin: 10px 20px 30px 40px;  /* 上 右 下 左（顺时针） */
}
```

`padding`、`border-width`、`border-radius` 同理。

### 9.2 width 的真实含义（最大的坑）

```css
.box {
  width: 320px;
  padding: 16px;
  border: 3px solid #2563eb;
}
```

你写了 320，但这个盒子**实际占位 358px**：

```
320（内容）+ 16×2（padding）+ 3×2（border）= 358
```

因为默认 `box-sizing: content-box`——`width` 只算内容区。

后果很典型：算好三个 320px 的卡片放在 960px 容器里，实际总宽 1074px，最后一张掉到下一行。

### 9.3 一行修好：box-sizing

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

打开之后，`width: 320px` 就是**整个盒子的宽度**，padding 和 border 从里面扣：

```
320 = 内容 + 16×2 + 3×2  →  内容 = 282px
```

现在三个 320px 卡片正好放进 960px 容器。**所有现代项目都有这一行**，包括所有 CSS 框架。

### 9.4 margin 合并（不是 bug，是规范）

**垂直方向相邻的 margin 会合并，取较大值，不是相加。**

```css
.a { margin-bottom: 20px; }
.b { margin-top: 30px; }
```

```html
<div class="a">A</div>
<div class="b">B</div>
```

两者之间是 **30px**，不是 50px。

**三种合并场景**：

1. 相邻兄弟元素之间
2. 父元素和第一个/最后一个子元素之间（父元素没有 padding/border 时，子元素的 margin 会"漏"到父元素外面）
3. 空块级元素自己的上下 margin

**不合并的情况**：`display: flex` / `grid` 的子元素、`overflow` 不为 `visible`、有 `padding`/`border` 隔开。

**对策** — 布局间距优先用 `gap`（flex 里）或只给一个方向（统一 `margin-bottom`）。别同时写上下 margin 然后靠合并算。

### 9.5 margin 还是 padding

| 用 | 什么时候 |
|---|---|
| `padding` | 间距应该在**背景色内部**（卡片内文字离边框的距离） |
| `margin` | 间距应该在**盒子外部**（两个卡片之间的距离） |

判断方法：给盒子加个背景色，间距被染上色的就是 padding，没染色的就是 margin。

### 9.6 居中三板斧

```css
/* 1. 块级元素水平居中：定宽 + 左右 auto */
.container {
  max-width: 720px;
  margin: 0 auto;
}

/* 2. 行内内容水平居中 */
.center { text-align: center; }

/* 3. 任意内容水平垂直居中（flex） */
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```

第 1 条是整站布局最常用的手法，记住它。

### 验收

1. 造两个盒子，分别设 `padding: 20px` 和 `margin: 20px`，加背景色观察差异
2. 关掉 `box-sizing: border-box`，对比同一个 `width: 320px` 盒子的实际宽度
3. 做两个相邻盒子，`margin-bottom: 40px` / `margin-top: 24px`，用 F12 量出实际间距是 40 而不是 64

---

## 第 10 章 display 与文档流

### 10.1 标准流

不写任何布局代码时，元素按**标准流**排列：

- 块级元素：从上到下，一个占一行，宽度默认撑满父元素
- 行内元素：从左到右，排满一行换行

标准流是默认行为，**大部分页面 80% 的布局靠标准流 + 一点 margin 就够**，不需要一上来就 flex。

### 10.2 display 的取值

| 值 | 行为 | 能设 width/height | 默认代表 |
|---|---|---|---|
| `block` | 独占一行，宽度撑满父元素 | ✅ | `div` `p` `h1` `ul` `section` |
| `inline` | 跟着文字流，不换行 | ❌ | `span` `a` `strong` `em` |
| `inline-block` | 不换行，但能设宽高 | ✅ | `img` `button` `input` |
| `flex` | 自身块级，子元素变成 flex 项 | ✅ | 手动设 |
| `inline-flex` | 自身行内，子元素是 flex 项 | ✅ | 手动设 |
| `none` | 完全消失，**不占位** | — | 配合 JS |

改成 `flex` 只影响**子元素**的排布，不改变元素自身是块级还是行内。

### 10.3 行内元素的特殊性

```css
span {
  width: 100px;      /* ❌ 无效 */
  height: 100px;     /* ❌ 无效 */
  margin-top: 20px;  /* ❌ 无效（垂直方向不生效） */
  margin-left: 20px; /* ✅ 生效 */
  padding: 10px;     /* ⚠️ 水平会撑开，垂直会溢出但不影响行高 */
  border: 1px solid; /* ✅ 会画出来 */
}
```

这就是"给 `span` 设宽度没反应"的原因。三种解法：

```css
span { display: inline-block; }  /* 最常用 */
span { display: block; }         /* 变成块级 */
/* 或者：换成 div */
```

### 10.4 position 定位

| 值 | 行为 |
|---|---|
| `static` | 默认，按标准流走，`top/left` 无效 |
| `relative` | 相对**自己原来的位置**偏移，原位置仍然保留 |
| `absolute` | 相对**最近的非 static 祖先**定位，脱离文档流（不占位） |
| `fixed` | 相对**视口**定位，滚动不动 |
| `sticky` | 滚动到阈值前正常，到了就粘住 |

```css
.badge {
  position: absolute;
  top: 8px;
  right: 8px;
}
.card { position: relative; }   /* 关键：给绝对定位一个参照 */
```

**最常见的坑** — 用了 `absolute` 但父元素没有 `position: relative`，于是它相对整个页面定位，跑到奇怪的地方。

**吸顶导航**：

```css
nav {
  position: sticky;
  top: 0;
  background: #fff;
  z-index: 10;
}
```

### 验收

1. 把 `.inline-demo` 改成 `display: inline-block` 并设 `width: 200px`，看是否生效
2. 写三个 `display: inline` 的 span，尝试设宽高，确认无效
3. 用 `position: sticky` 做一个吸顶导航
4. 做一个卡片，右上角绝对定位一个角标

---

## 第 11 章 flex 布局（重点）

flex 是现代 CSS 布局的主力。**先掌握它，别学 float 那一套老办法。**

### 11.1 主轴和交叉轴

```css
.row { display: flex; }
```

给容器加上 `display: flex` 后，它的**直接子元素**自动排成一行。引入两个概念：

- **主轴（main axis）**：默认**水平**。`justify-content` 控制主轴上的分布
- **交叉轴（cross axis）**：默认**垂直**。`align-items` 控制交叉轴上的对齐

```css
.container {
  display: flex;
  flex-direction: row;  /* 默认：主轴水平，从左到右 */
  /* column：主轴垂直，从上到下 */
}
```

**记住这张对应关系，flex 就不会乱**：默认情况下 `justify-content` 管水平，`align-items` 管垂直。改了 `flex-direction: column` 就反过来。

### 11.2 justify-content（主轴分布）

```css
justify-content: flex-start;    /* 默认，靠左 */
justify-content: flex-end;      /* 靠右 */
justify-content: center;        /* 居中 */
justify-content: space-between; /* 两端顶格，中间均分（导航栏） */
justify-content: space-around;  /* 每项两侧都有空隙 */
justify-content: space-evenly;  /* 所有间隙完全相等 */
```

最常用：`center` 和 `space-between`。

### 11.3 align-items（交叉轴对齐）

```css
align-items: stretch;     /* 默认，撑满容器高度 */
align-items: flex-start;  /* 顶部对齐 */
align-items: flex-end;    /* 底部对齐 */
align-items: center;      /* 垂直居中 */
```

**默认值是 `stretch`**，所以 flex 容器里的卡片高度会自动拉齐——这通常正是你要的效果（同排卡片等高）。

### 11.4 子项属性

```css
.item {
  flex-grow: 1;     /* 有剩余空间时按比例放大，0 = 不放大 */
  flex-shrink: 1;   /* 空间不够时按比例缩小，0 = 绝不缩小 */
  flex-basis: auto; /* 分配前的基准尺寸 */

  flex: 1;          /* 简写 = 1 1 0%：平分剩余空间 */
}
```

**`flex: 1` 是最常用的写法**，让所有子项平分容器宽度。

```css
.card { flex: 1 1 200px; }   /* 基准 200px，可伸可缩 */
```

配合 `flex-wrap: wrap`，就是响应式卡片列表的标准做法。

### 11.5 gap 和 wrap

```css
.container {
  display: flex;
  gap: 16px;          /* 子项之间统一间距，比给每个子项写 margin 干净 */
  row-gap: 16px;      /* 行间距 */
  column-gap: 16px;   /* 列间距 */
  flex-wrap: wrap;    /* 放不下自动换行；默认 nowrap 会挤压 */
}
```

`gap` 只作用于**子项之间**，不会在首尾外侧加空隙，这是它比 margin 好的地方。

### 11.6 六个常用配方

**① 水平垂直居中**

```css
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```

**② 导航栏：左 logo 右菜单**

```css
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 20px;
}
```

**③ 卡片网格（响应式）**

```css
.grid { display: flex; flex-wrap: wrap; gap: 16px; }
.grid > * { flex: 1 1 240px; }
```

**④ 左右两栏（侧栏固定，主内容自适应）**

```css
.layout { display: flex; gap: 24px; }
.sidebar { flex: 0 0 200px; }   /* 不放大不缩小，固定 200 */
.content { flex: 1; }           /* 吃掉剩下的 */
```

**⑤ 图标配文字**

```css
.icon-text { display: flex; align-items: center; gap: 8px; }
```

**⑥ 页脚吸底**

```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
main { flex: 1; }   /* 主内容撑开，把 footer 推到底 */
```

### 验收

1. 用 flex 做一个导航栏：左边站点名，右边三个链接，垂直居中
2. 用 `flex: 1 1 240px` + `gap` 做一排卡片，缩窗口确认能自动换行
3. 用 flex 做左右两栏，侧栏 200px 固定，主区自适应
4. 一个 `min-height: 100vh` 的容器，让一行字垂直水平居中

---

## 第 12 章 层叠与优先级

### 12.1 为什么会有冲突

```css
p          { color: green; }
.text-blue { color: blue; }
#intro     { color: red; }
```

```html
<p id="intro" class="text-blue">这段话是什么颜色？</p>
```

答案是**红色**。浏览器按固定规则裁决，这个规则叫**层叠（cascade）**。

### 12.2 权重计算

| 来源 | 分值 |
|---|---|
| 行内样式 `style="..."` | 1000 |
| ID 选择器 `#id` | 100 |
| 类、属性、伪类 `.class` `[attr]` `:hover` | 10 |
| 元素、伪元素 `p` `::before` | 1 |
| `*` 通配 | 0 |

**相加比较**：`.a.b.c` 是 30，`#x` 是 100，`#x` 更大。

### 12.3 同分时写在后面的赢

```css
.text-blue { color: blue; }
.text-blue { color: red; }   /* 这行赢，因为在后面 */
```

所以 CSS 的书写顺序有意义。建议的组织顺序：

1. 变量（`:root`）
2. 全局重置（`*`、`body`）
3. 通用元素（`h1`、`p`、`a`）
4. 组件类（`.card`、`.nav`）
5. 修饰类（`.card-wide`）
6. 响应式媒体查询（放最后才能覆盖前面）

### 12.4 !important

```css
p { color: red !important; }   /* 强制最高优先级 */
```

**只在两种情况用**：覆盖第三方库的样式、覆盖行内样式（没有别的办法时）。

如果 `!important` 变成日常手段，说明选择器结构已经坏了。正确做法是**降低被覆盖规则的权重**或调换顺序，而不是加 `!important`——它会引发军备竞赛。

### 12.5 继承

| 会继承 | 不会继承 |
|---|---|
| `color` | `margin` / `padding` / `border` |
| `font-family` / `font-size` / `font-weight` | `background` |
| `line-height` | `width` / `height` |
| `text-align` | `display` / `position` |

所以给 `body` 设 `font-family` 和 `color`，全站文字跟着变——最省事的做法。

手动控制：

```css
.child { color: inherit; }   /* 强制继承父元素的值 */
.child { color: initial; }   /* 恢复默认值 */
```

### 12.6 排查六步

样式没生效时，按顺序查：

1. **F12 → Elements → 选中元素 → Styles**，看目标属性在不在；被划掉说明被更高权重覆盖
2. **选择器写错了吗**：`.card` 写成 `.cards`、类名拼错，不会报错，只是静默失效
3. **文件真的加载了吗**：Network 面板看 `style.css` 是不是 404
4. **是不是被缓存了**：`Ctrl+F5`
5. **属性名拼错了吗**：`colr`、`paddin` 同样静默失效
6. **是不是写在错误的元素上**：父元素的 `width` 不影响子元素

### 验收

给同一个 `p` 同时写标签、类、ID 三条 `color`，先预测谁赢，再用 F12 验证。删掉 ID 那条，观察变化。

---

## 第 13 章 响应式

### 13.1 viewport（必写）

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

不写这行，手机浏览器会假装自己是 980px 宽的桌面屏，然后把页面缩小——文字小到看不清。**这是所有响应式的前提。**

### 13.2 媒体查询

```css
/* 默认样式：适合手机（移动优先） */
.container { padding: 16px; }

/* 屏幕宽度 ≥ 640px 时生效 */
@media (min-width: 640px) {
  .container { padding: 24px; }
}

/* 屏幕宽度 ≥ 1024px 时生效 */
@media (min-width: 1024px) {
  .container { max-width: 960px; margin: 0 auto; }
}
```

**移动优先**：先写手机上的样式（最简单），再用 `min-width` 逐步增强。反过来用 `max-width` 写桌面版再砍，代码会更乱。

常用断点（不必照抄，看内容什么时候挤坏了就在那加）：

```css
@media (min-width: 640px)  { }  /* 大手机 / 小平板 */
@media (min-width: 768px)  { }  /* 平板 */
@media (min-width: 1024px) { }  /* 桌面 */
```

### 13.3 相对单位

| 单位 | 相对什么 | 用途 |
|---|---|---|
| `px` | 绝对像素 | 边框、小间距 |
| `rem` | 根元素字号（默认 16px） | 字号、大间距（推荐） |
| `em` | **当前元素**字号 | 少用，容易连锁 |
| `%` | 父元素对应尺寸 | 宽度 |
| `vh` / `vw` | 视口高度/宽度 1% | 全屏区块 |
| `dvh` | 动态视口高度 | 移动端全屏（比 vh 准） |

```css
h1 { font-size: 2rem; }   /* 32px */
p  { font-size: 1rem; }   /* 16px */
```

`rem` 的好处：用户改了浏览器默认字号，整站等比缩放，无障碍更好。

### 13.4 图片自适应

```css
img {
  max-width: 100%;   /* 不超过容器宽度 */
  height: auto;      /* 保持宽高比 */
  display: block;    /* 去掉底部基线空隙 */
}
```

### 13.5 一行做响应式字号

```css
h1 { font-size: clamp(24px, 5vw, 40px); }
```

`clamp(最小值, 弹性值, 最大值)`：窄屏 24px，宽屏最多 40px，中间按视口宽度缩放。不用写媒体查询。

### 13.6 检查方法

F12 左上角设备图标（`Ctrl+Shift+M`）切到 iPhone 尺寸，检查：

- 有没有横向滚动条（有就说明有元素超宽）
- 文字是否可读
- 卡片是否挤在一起

### 验收

在手机尺寸下检查你的页面，修掉横向滚动条，确保卡片单列显示、导航可用。

---

## 第 14 章 二十个必须知道的坑

| # | 现象 | 原因 / 解法 |
|---|---|---|
| 1 | 中文乱码 | 文件存 UTF-8 + `<meta charset="UTF-8">` |
| 2 | 页面有白边 | `body` 默认 8px 外边距，写 `margin: 0` |
| 3 | 改了没变化 | `Ctrl+F5` 强刷；或者样式文件 404 |
| 4 | 盒子比预期宽 | 忘了 `box-sizing: border-box` |
| 5 | 给 `span` 设宽高无效 | 它是 `inline`，改 `inline-block` |
| 6 | 上下间距不是两者相加 | margin 合并，取较大值 |
| 7 | 样式被覆盖 | F12 看哪条被划掉，检查权重 |
| 8 | `height: 100%` 无效 | 父元素没定高，用 `vh` 或 `min-height` |
| 9 | 图片下面有几像素空隙 | `img { display: block }` |
| 10 | flex 子项挤在一起 | 加 `gap`，或加 `flex-wrap: wrap` |
| 11 | flex 子项不换行 | 默认 `nowrap`，要写 `wrap` |
| 12 | 文字溢出盒子 | `overflow: hidden` / `text-overflow: ellipsis` |
| 13 | 出现横向滚动条 | 有元素超宽，常见于 `width: 100vw` 或负 margin |
| 14 | 链接点完变紫色 | 浏览器默认 `:visited`，写 `a { color: ... }` 覆盖 |
| 15 | `p` 里的 `div` 跑出去了 | `p` 不能含块级元素，换成 `div` |
| 16 | 本地好好的，上线 404 | Windows 不区分文件名大小写，Linux 区分 |
| 17 | 图片/CSS 加载失败 | 相对路径写错，F12 Network 看红字 |
| 18 | `absolute` 跑到奇怪位置 | 父元素缺 `position: relative` |
| 19 | `!important` 越用越多 | 选择器结构坏了，回去简化权重 |
| 20 | 手机上字特别小 | 缺 viewport meta，或字号用了过小的 px |

---

## 第 15 章 实战：个人主页

### 15.1 需求

单页个人主页：

- 头部：名字 + 一句话简介 + 几个链接按钮
- "关于我"区块：几段自我介绍
- "项目与战绩"区块：三张卡片
- 页脚：联系方式
- 手机上单列，桌面上卡片三列

### 15.2 先规划结构，再写代码

```
<html>
  <head>  编码、标题、样式链接
  <body>
    <header class="hero">
      名字 / 简介 / 链接
    </header>
    <main>
      <section class="about">  关于
      <section id="works">     卡片 ×3
    </main>
    <footer>  联系方式
```

**养成习惯：先写纯内容骨架，确认结构对了再加 CSS。** 一次性写 HTML 和 CSS，调试时分不清是结构问题还是样式问题。

### 15.3 完整代码

新建 `E:\website\me.html`，粘贴后打开看效果，**再逐块改动理解**。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>杨渝渝 · 算法竞赛</title>
  <style>
    :root {
      --main: #2563eb;
      --text: #1f2937;
      --muted: #6b7280;
      --bg: #f8fafc;
      --card: #ffffff;
      --line: #e5e7eb;
    }

    *, *::before, *::after { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: system-ui, -apple-system, "Segoe UI", "Microsoft YaHei", sans-serif;
      color: var(--text);
      background: var(--bg);
      line-height: 1.8;
    }

    img { max-width: 100%; display: block; }
    a { color: var(--main); text-decoration: none; }
    a:hover { text-decoration: underline; }

    .wrap {
      max-width: 860px;
      margin: 0 auto;
      padding: 0 20px;
    }

    /* ---------- 头部 ---------- */
    .hero {
      padding: 72px 0 56px;
      text-align: center;
      background: linear-gradient(180deg, #eef2ff 0%, var(--bg) 100%);
    }
    .hero h1 {
      margin: 0 0 8px;
      font-size: clamp(26px, 5vw, 36px);
      letter-spacing: -0.5px;
    }
    .hero p {
      margin: 0 0 20px;
      color: var(--muted);
      font-size: 17px;
    }
    .hero-links {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 10px;
    }
    .btn {
      padding: 8px 18px;
      border: 1px solid var(--line);
      border-radius: 999px;
      background: var(--card);
      font-size: 14px;
      transition: all 0.2s ease;
    }
    .btn:hover {
      border-color: var(--main);
      color: var(--main);
      text-decoration: none;
    }

    /* ---------- 区块通用 ---------- */
    section { padding: 44px 0; }
    section h2 {
      font-size: 20px;
      margin: 0 0 20px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--line);
    }

    /* ---------- 关于 ---------- */
    .about p { margin: 0 0 12px; color: #374151; }

    /* ---------- 卡片 ---------- */
    .cards {
      display: flex;
      flex-wrap: wrap;
      gap: 16px;
    }
    .card {
      flex: 1 1 240px;
      padding: 20px;
      background: var(--card);
      border: 1px solid var(--line);
      border-radius: 10px;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .card:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
    }
    .card h3 { margin: 0 0 8px; font-size: 16px; }
    .card p { margin: 0; color: var(--muted); font-size: 14px; line-height: 1.7; }

    /* ---------- 页脚 ---------- */
    footer {
      margin-top: 24px;
      padding: 32px 0;
      border-top: 1px solid var(--line);
      text-align: center;
      color: var(--muted);
      font-size: 14px;
    }
  </style>
</head>

<body>
  <header class="hero">
    <div class="wrap">
      <h1>杨渝渝</h1>
      <p>算法竞赛选手 · C++</p>
      <div class="hero-links">
        <a class="btn" href="https://codeforces.com" target="_blank" rel="noopener">Codeforces</a>
        <a class="btn" href="mailto:me@example.com">邮件</a>
        <a class="btn" href="#works">看项目</a>
      </div>
    </div>
  </header>

  <main class="wrap">
    <section class="about">
      <h2>关于我</h2>
      <p>在练算法竞赛，日常刷 Codeforces 和 AtCoder，主要用 C++。</p>
      <p>这里会放我的题解、训练记录和踩过的坑。</p>
    </section>

    <section id="works">
      <h2>项目与战绩</h2>
      <div class="cards">
        <article class="card">
          <h3>这个网站</h3>
          <p>手写的 HTML + CSS，没有用任何框架。目的是把基础打牢。</p>
        </article>
        <article class="card">
          <h3>算法笔记</h3>
          <p>按主题整理的模板和易错点，覆盖图论、数据结构、数论。</p>
        </article>
        <article class="card">
          <h3>对拍工具</h3>
          <p>随机数据生成 + 双程序比对，用来验证写出来的解法。</p>
        </article>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap">
      我是页脚 · 2026
    </div>
  </footer>
</body>
</html>
```

### 15.4 逐块理解

带着问题读代码，别只是看：

1. **`.wrap` 为什么能居中？** `max-width` + `margin: 0 auto`（第 9.6 节）
2. **为什么全站字体只写了一次？** `body` 的 `font-family` 会继承（第 12.5 节）
3. **三张卡片为什么能换行？** `flex-wrap: wrap` + 子项 `flex: 1 1 240px`（第 11.5 节）
4. **`clamp(26px, 5vw, 36px)` 干什么？** 响应式字号（第 13.5 节）
5. **为什么要 `* { box-sizing: border-box }`？** 否则 padding 会撑破卡片（第 9.2 节）
6. **`.btn:hover` 为什么要写 `text-decoration: none`？** 全局 `a:hover` 有下划线，按钮上不想要（第 12.3 节）

### 15.5 改造任务

按顺序做，每做完一项刷新看效果：

1. 改 `--main` 成你喜欢的颜色，全站应该跟着变
2. 把三张卡片改成四张，观察布局怎么变
3. 给 `.hero` 加头像图片（`border-radius: 50%` 变圆形）
4. 给 `.cards` 加 `flex-direction: column`，看会发生什么，然后改回来
5. 缩窗口到手机宽度，检查有没有横向滚动条
6. 加一个"练过的算法"区块，用 `ul` 列表
7. 给每个 `section` 加 `id`，在头部做锚点链接跳转
8. 把导航改成 `position: sticky` 吸顶

### 15.6 验收清单

- [ ] 双击打开无乱码
- [ ] F12 切手机尺寸，单列显示，无横向滚动条
- [ ] 改 `--main` 一个值，全站主色跟着变
- [ ] 所有链接可点，`target="_blank"` 的在新标签打开
- [ ] 卡片 hover 有反馈
- [ ] Elements 里结构是 `header` / `main` / `section` / `article` / `footer`，不是一堆 `div`

---

## 附录 A 速查表

### 选择器

```css
p             /* 标签 */
.card         /* 类 */
#main         /* ID */
h1, h2, h3    /* 群组 */
.card p       /* 后代 */
.card > p     /* 直接子 */
h2 + p        /* 紧邻兄弟 */
a:hover       /* 悬停 */
a:focus       /* 聚焦 */
p::first-line /* 伪元素 */
*             /* 全部 */
```

### 常用属性分类

```css
/* 尺寸 */
width  height  max-width  min-height
/* 盒模型 */
margin  padding  border  box-sizing
/* 排版 */
font-family  font-size  font-weight  line-height
letter-spacing  text-align  text-decoration  text-transform
/* 颜色 */
color  background-color  background  opacity
/* 装饰 */
border-radius  box-shadow
/* 布局 */
display  flex  flex-direction  justify-content
align-items  gap  flex-wrap  position
/* 溢出 */
overflow  white-space  text-overflow
/* 动效 */
transition  transform
```

### flex 速查

| 容器属性 | 值 |
|---|---|
| `display` | `flex` / `inline-flex` |
| `flex-direction` | `row` / `column` / `row-reverse` / `column-reverse` |
| `justify-content` | `flex-start` / `center` / `flex-end` / `space-between` / `space-around` / `space-evenly` |
| `align-items` | `stretch` / `flex-start` / `center` / `flex-end` |
| `flex-wrap` | `nowrap` / `wrap` |
| `gap` | 任意长度 |

| 子项属性 | 含义 |
|---|---|
| `flex: 1` | 平分剩余空间 |
| `flex: 0 0 200px` | 固定 200px，不伸不缩 |
| `flex: 1 1 240px` | 基准 240px，可伸可缩 |
| `align-self` | 单独覆盖父容器的 `align-items` |

### 单位

| 单位 | 说明 |
|---|---|
| `px` | 像素，固定 |
| `rem` | 相对根字号（16px 基准） |
| `%` | 相对父元素 |
| `vh` / `vw` | 相对视口 1% |
| `dvh` | 动态视口高度，移动端更准 |
| `clamp(a, b, c)` | 最小 a，理想 b，最大 c |

### 颜色速记

```css
#fff        白        #000        黑
#f8fafc     极浅灰底   #e5e7eb     边框灰
#1f2937     正文深灰   #6b7280     次要文字灰
#2563eb     常用蓝     #dc2626     警告红
```

---

## 附录 B 标签索引 A–Z

按字母查，一行看懂每个标签是干什么的。

| 标签 | 含义 | 关键点 |
|---|---|---|
| `<a>` | 超链接 | `href` 必填；外链加 `rel="noopener"` |
| `<abbr>` | 缩写 | `title` 放全称，悬停显示 |
| `<address>` | 联系方式 | 只放联系信息，默认斜体 |
| `<article>` | 独立完整的内容 | 单独拿出去也成立 |
| `<aside>` | 侧栏 / 补充内容 | 去掉不影响主内容 |
| `<audio>` | 音频 | 要加 `controls` |
| `<b>` | 视觉加粗 | 无语义，优先用 `strong` |
| `<blockquote>` | 块级引用 | 默认缩进 |
| `<body>` | 页面可见内容 | 只能有一个 |
| `<br>` | 强制换行 | 只在文字内部用，别当间距 |
| `<button>` | 按钮 | 表单内不写 `type` 默认是 `submit` |
| `<canvas>` | 位图画布 | 靠 JS 绘制 |
| `<caption>` | 表格标题 | 必须紧跟 `<table>` |
| `<cite>` | 作品名 | 默认斜体 |
| `<code>` | 行内代码 | 等宽字体 |
| `<dd>` | 定义列表的描述 | 跟在 `<dt>` 后 |
| `<del>` | 已删除内容 | 可带 `datetime` |
| `<details>` | 可折叠块 | 配 `<summary>`，无需 JS |
| `<div>` | 块级通用容器 | 无语义，布局用 |
| `<dl>` | 定义列表 | 术语 + 解释的配对 |
| `<dt>` | 定义列表的术语 | — |
| `<em>` | 语气强调 | 默认斜体，有语义 |
| `<fieldset>` | 表单分组 | 配 `<legend>` |
| `<figcaption>` | 图注 | 放在 `<figure>` 内 |
| `<figure>` | 独立内容单元 | 图 + 说明的组合 |
| `<footer>` | 页脚 | 版权、联系方式 |
| `<form>` | 表单容器 | 静态站没有后端，提交无效 |
| `<h1>`–`<h6>` | 标题层级 | 一页一个 `h1`，不跳级 |
| `<head>` | 元信息容器 | 内容不显示 |
| `<header>` | 页眉 | 标题、logo、导航 |
| `<hr>` | 主题分隔线 | 装饰线用 CSS `border` |
| `<html>` | 根元素 | 带 `lang` 属性 |
| `<i>` | 视觉斜体 | 无语义，优先 `em`；也用于图标 |
| `<iframe>` | 嵌入外部页面 | 必须写 `title` |
| `<img>` | 图片 | `src` + `alt` 必写 |
| `<input>` | 输入控件 | 行为由 `type` 决定；无 `name` 不提交 |
| `<ins>` | 新增内容 | 常配合 `<del>` |
| `<kbd>` | 键盘按键 | 等宽字体 |
| `<label>` | 表单控件说明 | `for` 必须等于控件的 `id` |
| `<legend>` | 分组标题 | 放在 `<fieldset>` 内 |
| `<li>` | 列表项 | 父元素只能是 `ul`/`ol` |
| `<link>` | 引入外部资源 | 常用 `rel="stylesheet"` |
| `<main>` | 主体内容 | 一页只能一个 |
| `<mark>` | 高亮 | 默认黄底 |
| `<meta>` | 元信息 | `charset`、`viewport` |
| `<nav>` | 导航链接组 | 只用于主要导航 |
| `<ol>` | 有序列表 | 自动编号，`start` / `type` |
| `<optgroup>` | 下拉分组 | `label` 属性 |
| `<option>` | 下拉选项 | `value` 是提交值 |
| `<p>` | 段落 | 不能含块级元素 |
| `<pre>` | 预格式化文本 | 保留空格换行 |
| `<q>` | 行内引用 | 自动加引号 |
| `<s>` | 删除线 | 视觉删除，语义用 `del` |
| `<section>` | 有主题的分节 | 通常带标题 |
| `<select>` | 下拉选择 | 配 `<option>` |
| `<small>` | 小字 | 附属说明 |
| `<source>` | 媒体源 | `video`/`audio` 多格式 |
| `<span>` | 行内通用容器 | 无语义；宽高默认无效 |
| `<strong>` | 重要内容 | 默认加粗，有语义 |
| `<style>` | 内部样式表 | 内容写 CSS |
| `<sub>` | 下标 | — |
| `<summary>` | 折叠标题 | `<details>` 里始终可见 |
| `<sup>` | 上标 | — |
| `<svg>` | 矢量图形 | 缩放不糊 |
| `<table>` | 表格 | 只用于数据，不做布局 |
| `<tbody>` | 表体 | — |
| `<td>` | 普通单元格 | `colspan` / `rowspan` 合并 |
| `<textarea>` | 多行文本 | `rows` / `cols` |
| `<tfoot>` | 表尾 | 汇总行 |
| `<th>` | 表头单元格 | 默认加粗居中 |
| `<thead>` | 表头区 | — |
| `<time>` | 时间 | `datetime` 给机器读 |
| `<title>` | 页面标题 | 显示在浏览器标签页 |
| `<tr>` | 表格行 | — |
| `<u>` | 下划线 | 语义是"标注"，不是链接样式 |
| `<ul>` | 无序列表 | 直接子元素只能是 `li` |
| `<video>` | 视频 | 不加 `controls` 就没有按钮 |
| `<wbr>` | 可选换行点 | 长单词/长 URL 断行 |

---

## 附录 C 学习路线与上线

### 学习节奏

| 阶段 | 内容 | 时间 | 产出 |
|---|---|---|---|
| 1 | 第 0–6 章（HTML 全部） | 5–6 小时 | 结构正确、语义清楚的纯内容页面 |
| 2 | 第 7–10 章（CSS 基础 + 盒模型） | 4 小时 | 加了样式、能看的多页站 |
| 3 | 第 11 章（flex） | 2 小时 | 会做导航、卡片、两栏布局 |
| 4 | **上线**（git + GitHub Pages） | 1–2 小时 | 一个真实可访问的网址 |
| 5 | 第 12–13 章（优先级 + 响应式） | 2 小时 | 手机上能看 |
| 6 | 第 15 章实战改造 | 2 小时 | 自己的个人主页 |

**关键提醒：第 4 步不要延后。** 常见失败是憋着做一个"完美"的站，三个月没上线，然后放弃。先让一个丑但能访问的版本存在，后面全是增量改进。

### 上线三步

```bash
# 1. 初始化仓库（在 E:\website 目录下）
git init
git add .
git commit -m "first commit"

# 2. 推到 GitHub（先在网页上建个空仓库，或用 gh）
git remote add origin https://github.com/<用户名>/<仓库名>.git
git branch -M main
git push -u origin main

# 3. 网页操作：仓库 → Settings → Pages → Source 选 "GitHub Actions" → 选 Static HTML 模板
```

地址是 `https://<用户名>.github.io/<仓库名>/`。

**注意** — GitHub Pages 是子路径部署，图片和 CSS 要用相对路径（`style.css` 而不是 `/style.css`），否则 404。

### 学完之后再学什么

按需要，不用提前：

- **`grid` 布局**：比 flex 强，做整页二维布局更顺，flex 上手后再学
- **Tailwind CSS**：utility class 写法，写快了但可读性靠习惯
- **Astro / Hugo**：把 Markdown 自动转成页面，写博客的正确姿势
- **一点 JavaScript**：暗色模式切换、移动端菜单展开，个人站最常见的两个 JS 需求
- **域名**：买一个，DNS 加 CNAME 指向托管平台，开 HTTPS。约 ¥30–80/年

**不要提前学**：React / Vue / 打包工具 / TypeScript。静态个人站用不上，学了只会拖慢进度。

---

*最后更新：2026-10-20 · v2 详解版*

---

## 附录 D 暂缓内容（用到再看）

下面这些是从正文里移出来的，**你现在完全不需要**。等某个具体需求出现了，再翻到这里。

---

### 视频与音频

#### 视频 `<video>` 与音频 `<audio>`

**`<video>` 属性** —

| 属性 | 作用 |
|---|---|
| `src` | 视频地址（也可以用子元素 `<source>`） |
| `controls` | 显示播放控件（**不写就没有任何按钮**） |
| `autoplay` | 自动播放（多数浏览器要求同时有 `muted`） |
| `muted` | 静音 |
| `loop` | 循环播放 |
| `poster` | 封面图 |
| `playsinline` | iOS 上不自动全屏 |
| `preload` | `none` / `metadata` / `auto` |

```html
<video src="demo.mp4" controls width="480" poster="cover.jpg" playsinline>
  你的浏览器不支持 video 标签。
</video>
```

**多个格式（浏览器兼容）**：

```html
<video controls>
  <source src="demo.webm" type="video/webm">
  <source src="demo.mp4" type="video/mp4">
  你的浏览器不支持 video。
</video>
```

**`<audio>`** 同理，属性更少：`src` `controls` `autoplay` `loop` `muted` `preload`。

```html
<audio src="bgm.mp3" controls></audio>
```

**注意** —

- **不加 `controls` 就完全无法操作**，新手最常见的"视频不显示按钮"
- `autoplay` 不带 `muted` 基本都会被浏览器拦截
- 浏览器**不会**自动循环播放带声音的内容，别指望做背景音乐

#### 嵌入外部页面 `<iframe>`

**含义** — 在页面里嵌入另一个页面。

```html
<iframe src="https://example.com" width="600" height="400" title="示例"></iframe>
```

**注意** —

- 有安全和性能代价，只在必须时用（地图、视频播放器、代码演示）
- 有些站点禁止被嵌入（会用 `X-Frame-Options` 拒绝）
- 始终写 `title` 属性（无障碍要求）

#### 图形 `<svg>` 和 `<canvas>`

- **`<svg>`**：矢量图形，可以直接写进 HTML。图标、Logo 用它。**缩放不糊**。
- **`<canvas>`**：位图画布，靠 JS 绘制。做数据可视化、游戏。

个人主页基本用不到，做图标时优先用 SVG。

---

### 表格与表单（原第 5 章）

#### 表格结构

**完整骨架**：

```html
<table>
  <caption>最近三场比赛</caption>
  <thead>
    <tr>
      <th scope="col">比赛</th>
      <th scope="col">过题数</th>
      <th scope="col">排名</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>牛客多校</td>
      <td>3</td>
      <td>1200</td>
    </tr>
    <tr>
      <td>Codeforces Round</td>
      <td>4</td>
      <td>800</td>
    </tr>
  </tbody>
</table>
```

| 标签 | 含义 |
|---|---|
| `<table>` | 表格容器 |
| `<caption>` | 表格标题（必须紧跟 `table` 开始标签） |
| `<thead>` | 表头区 |
| `<tbody>` | 表体区（可以有多个） |
| `<tfoot>` | 表尾区（汇总行） |
| `<tr>` | 一行 table row |
| `<th>` | 表头单元格，**默认加粗居中** |
| `<td>` | 普通单元格 |

**合并单元格**：

```html
<td colspan="2">横跨两列</td>
<td rowspan="3">竖跨三行</td>
```

**默认表现** — 表格不显示边框（这是浏览器默认），单元格内容左对齐、表头居中。加边框：

```css
table { border-collapse: collapse; width: 100%; }
th, td { border: 1px solid #e5e7eb; padding: 8px 12px; text-align: left; }
```

`border-collapse: collapse` 让相邻单元格的边框合并成一条，否则会出现双线。

**注意** —

- 表格**只用于展示表格数据**，不要拿来排版（二十年前的做法）
- 移动端宽表格会溢出，用外层容器 `overflow-x: auto` 加横向滚动

#### 表单 `<form>`

**含义** — 收集用户输入的容器。

**关键属性** —

| 属性 | 作用 |
|---|---|
| `action` | 提交到哪个地址 |
| `method` | `get`（参数在 URL）/ `post`（在请求体） |

```html
<form action="/submit" method="post">
  ...
</form>
```

**静态站没有后端，表单提交不会有结果。** 个人站要收留言，用第三方服务（Formspree 等）或者干脆只放邮箱链接。

#### 输入框 `<input>`

**含义** — 单行输入控件。空元素，行为完全由 `type` 决定。

**`type` 全表**：

| type | 外观/行为 |
|---|---|
| `text` | 单行文本（默认） |
| `password` | 密码，输入显示圆点 |
| `email` | 邮箱，自带格式校验 |
| `number` | 数字，带上下箭头 |
| `tel` | 电话，移动端弹数字键盘 |
| `url` | 网址，自带校验 |
| `search` | 搜索框 |
| `date` | 日期选择器 |
| `time` | 时间 |
| `datetime-local` | 日期 + 时间 |
| `month` / `week` | 月 / 周 |
| `color` | 颜色选择器 |
| `range` | 滑块 |
| `file` | 文件选择 |
| `checkbox` | 复选框（可多选） |
| `radio` | 单选框（同 `name` 互斥） |
| `submit` | 提交按钮 |
| `reset` | 重置按钮 |
| `button` | 普通按钮（要配 JS） |
| `hidden` | 隐藏字段，随表单提交 |
| `image` | 图片按钮 |

**常用属性**：

| 属性 | 作用 |
|---|---|
| `name` | 提交时的字段名（**没有 name 就不会被提交**） |
| `value` | 初始值 |
| `placeholder` | 灰色提示文字（不是默认值！） |
| `required` | 必填，空着不让提交 |
| `disabled` | 禁用，灰掉且不提交 |
| `readonly` | 只读，可选中可提交 |
| `checked` | 复选框/单选框默认选中 |
| `maxlength` / `minlength` | 字符数限制 |
| `min` / `max` / `step` | 数字范围与步长 |
| `pattern` | 正则校验 |
| `autocomplete` | 自动填充 |

```html
<label for="email">邮箱</label>
<input id="email" name="email" type="email" placeholder="you@example.com" required>

<label>
  <input type="checkbox" name="agree" checked> 我同意
</label>
```

**`placeholder` 不是默认值**：用户不输入时它不会提交，值也不会变。要默认值用 `value`。

#### 多行文本 `<textarea>`

```html
<label for="msg">留言</label>
<textarea id="msg" name="msg" rows="4" cols="40" placeholder="说点什么"></textarea>
```

`rows` 行数，`cols` 列数。尺寸一般用 CSS 控制（`width`、`resize: vertical`）。

#### 下拉选择 `<select>` / `<option>` / `<optgroup>`

```html
<select name="lang">
  <option value="">请选择</option>
  <optgroup label="竞赛">
    <option value="cpp">C++</option>
    <option value="py">Python</option>
  </optgroup>
</select>
```

`value` 是提交的值，标签之间是显示的文字。多个选择加 `multiple` 属性。

#### 标签 `<label>`（必写）

**含义** — 给表单控件关联一个可点击的文字说明。

**两种写法**：

```html
<!-- 1. for 指向 id -->
<label for="name">名字</label>
<input id="name" type="text">

<!-- 2. 包裹住控件 -->
<label>名字 <input type="text"></label>
```

**作用** — 点击文字就能聚焦输入框；屏幕阅读器会读出这个标签；复选框点文字也能勾选。

**注意** — 用 `for` 时，`for` 的值必须**完全等于**对应 `input` 的 `id`。

#### 按钮 `<button>`

```html
<button type="submit">提交</button>
<button type="button">普通按钮</button>
<button type="reset">重置</button>
```

**注意** — **在 `<form>` 里，不写 `type` 的 `button` 默认是 `submit`**，点一下会提交整个表单。只想做普通按钮时必须写 `type="button"`。这是很常见的坑。

#### 分组 `<fieldset>` + `<legend>`

```html
<fieldset>
  <legend>联系方式</legend>
  <label for="a">邮箱</label><input id="a" type="email">
  <label for="b">电话</label><input id="b" type="tel">
</fieldset>
```

`fieldset` 画一个框，`legend` 是框上的标题。表单较长时用来分组。

#### 验收

做一个"留言"表单：三个 `input`（text / email / checkbox）、一个 `textarea`、一个 `select`、一个 `button type="submit"`。要求每个控件都有对应的 `label`，点标签文字能聚焦到输入框。

---
