---
title: 文档风格指南
icon: markdown
date: 2023-07-20 23:46:54
updated: 2023-11-23 22:39:41
---

# 文档风格指南

## 文件命名

文档网站根据每个 Markdown 源文件的路径确定每个页面的路由。因而，确定文件名时应慎重，一旦确定，尽量不要再改动。
由于 Windows 不区分文件名大小写，故而 `option-B.md` 和 `option-b.md` 在 Windows 下会出现冲突。

我们使用的文件的命名规则是：

- 文件名一律采用小写字母
- 文件名应尽量使用单词全称，避免使用各种形式的简写
- 若文件名中含多个单词，应使用连字符 (hyphen) `-` 连接

## 文档 Frontmatter 规范

通过 Frontmatter 为每个 Markdown 页面引入配置。

Frontmatter 必须在 Markdown 文件的顶部，并且被包裹在一对三短划线中间。下面是一个基本的示例:

```md
---
title: 页面的标题
icon: markdown
author:
  - name: 作者1
    url: https://github.com/windingwind
  - name: 作者2
    url: https://northword.cn
  - name: 作者3
date: 2023-07-20 23:46:54
updated: 2023-07-21 18:39:41
---

<!-- 这里是 Markdown 内容 -->

...
```

下面是一些常用的 Frontmatter 键：

| 键         | 类型   | 必填 | 默认值         | 描述                                                                                                             |
| ---------- | ------ | ---- | -------------- | ---------------------------------------------------------------------------------------------------------------- |
| title      | string | 否   | 第一个一级标题 | 页面的标题。如果你不在 Frontmatter 中设置 title ，那么页面中第一个一级标题（即 # title）的内容会被当作标题使用。 |
| shortTitle | string | 否   | 标题           | 当前页面的短标题，会在导航栏、侧边栏和路径导航中作为首选。                                                       |
| icon       | string | 否   | 无             | 当前页面的图标                                                                                                   |
| author     | -      | 否   | -              | 见下述                                                                                                           |
| data       | string | 否   | 文件的创建日期 | 文档的创建日期                                                                                                   |
| update     | string | 否   | 文件的更新日期 | 该值其实无用，页面显示的最后更新时间是 Git 提交时间                                                              |

::: note `author` 详解

`author` 由一组 `author.name` 和 `author.url` / `author.email` 组成，其中 `url` 和 `email` 都是可选的。

尤其需要注意的是缩进，name 前空二格，加一个短横线 `-`，空一格。`url` 或 `email` 与 `name` 保持对齐，不需要加 `-`。

:::

::: details 更多的 Frontmatter 可以参考框架的文档

- [信息 Frontmatter 配置 | vuepress-theme-hope (vuejs.press)](https://theme-hope.vuejs.press/zh/config/frontmatter/info.html)
- [布局 Frontmatter 配置 | vuepress-theme-hope (vuejs.press)](https://theme-hope.vuejs.press/zh/config/frontmatter/layout.html#dir)

:::

## 文档语法风格

所有教程均采用 Markdown 语言编写，下面列出了一些本文档中可能用到的语法和注意事项。

### 标题

```md
# 一级标题

## 二级标题

### 三级标题

#### 四级标题
```

::: tip

一级标题是文档名，对应页面标题。一篇文档应有且只有一个一级标题

:::

- 文档内容从二级标题开始。
- 文档中标题级别应逐级递增，例如：二级标题内应跟随三级标题，而不能越过三级标题直接使用四级标题
- 标题不应含有特殊字符：如 latex 公式，代码块，数字编号等，不应以标点符号结尾
- 标题前后空一行。

### 正文文本

```md
正文段落 1
(空行)
正文段落 2
```

::: tip

- 中文字符与英文字符和数字之间应加上空格，如 `中文 ABC 中文` 而非 `中文ABC中文`
  `中文 123 中文` 而非 `中文123中文`
- 标点符号采用全角，如 `，`、`。`、`：`、`、`、`？` 等
  标点符号与中文字符、英文字符以及数字之间不需加空格
- 大小写应正确，如：`Zotero` 不是 `zotero`，`GitHub` 不是 `github`
- 正文中部分专有词和特殊符号，可以放入 [`行内代码`](#代码) 来表示，美观且不容易发生错误，例如：
  操作步骤：`编辑` - `首选项` - `引用` 。

:::

### 文字样式

```md
这是一段文本，
**用两对星号包裹的内容会被加粗**，
而*只用一对星号包裹的内容会显示为斜体*，
用~~两对波浪线包裹的内容会显示为删除~~，
上下标：19^th^ H~2~O，
你可以标记 ==重要的内容== 。
```

预览：
这是一段文本，
**用两对星号包裹的内容会被加粗**，
而*只用一对星号包裹的内容会显示为斜体*，
用~~两对波浪线包裹的内容会显示为删除~~，
上下标：19^th^ H~2~O，
你可以标记 ==重要的内容== 。

### 无序列表和有序列表

```md
#### 无序列表

- item 1
  - 更多的列表项
  - 更多的列表项
  - 更多的列表项
- item 2
- item 3

#### 有序列表

1. item 1
2. item 2
3. item 3
```

### 链接

```md
[相对路径访问主页](../README.md)

[相对路径访问贡献指南](./contributing.md)
```

### 图片

```md
![图片描述](../.vuepress/public/assets/icon/chrome-192.png)
```

::: tip

所有的图片资源都应放入 `src/assets` 内，尽量以通俗的方式描述图片内容。

:::

::: warning

我们不使用 HTML 语法 `<img>` 标签来引入图片，请使用标准的 Markdown 语法。

:::

### 视频

```md
一个 B 站视频:

<BiliBili bvid="BV1kt411o7C3" />

一个自定义空降地址的 B 站视频:

<BiliBili aid="34304064" cid="109293122" ratio="9:16" time="60" page="2" />
```

::: tip

受限于存储空间，文档不支持插入本地视频，引入视频请上传 bilibili，然后以以上语法引入视频。

:::

### 表格

使用 GitHub 风格表格：

```md
|     居中      |         右对齐 | 左对齐         |
| :-----------: | -------------: | :------------- |
| 居中使用`:-:` | 右对齐使用`-:` | 左对齐使用`:-` |
|       b       |      aaaaaaaaa | aaaa           |
|       c       |           aaaa | a              |
```

::: tip

第二行表示对其方式的 `:` 不是必须的，当没有时，会默认为居左。

:::

### 代码

#### 行内代码

```md
行内代码效果: `code`
```

行内代码效果: `code`

#### 块级代码

````md
```js
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
```
````

三个反引号后跟随代码块语言：`md`、`js`、`plain`（纯文本） 等。

预览：

```js
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
```

### 告示块

#### 提示

```md
::: tip

这是一个提示

:::
```

::: tip

这是一个提示

:::

#### 备注

```md
::: note

这是一个备注

:::
```

::: note

这是一个备注

:::

#### 注意

```md
::: warning

这是一个注意

:::
```

::: warning

这是一个注意

:::

#### 警告

```md
::: caution

这是一个警告

:::
```

::: caution

这是一个警告

:::

#### 详情

```md
::: details

这是一个折叠可见内容

:::
```

::: details

这是一个折叠可见内容

:::

#### 自定义标题

:::: tip 自定义标题

通过在 `tip`、`warning`、`caution`、`details` 后添加文字，可以自定义块标题，例如：

```md
::: tip 自定义标题

通过在 `tip`、`warning`、`caution`、`details` 后添加文字

:::
```

::::

#### 嵌套显示

支持两级嵌套，第一级的标志使用四个冒号`::::`，例如：

```md
:::: details 嵌套显示

::: tip

这是第二级提示。

:::

::::
```

:::: details 嵌套显示

::: tip

这是第二级提示。

:::

::::

### 脚注

```md
这是一段文本[^1]

[^1]: 这是一个脚注
```

脚注内容就近放置，以方便阅读源文本。

### 引用

```md
这是一段正文文本

> 这是一段引用文本

这是另一段正文文本
```

::: tip

除上述文字样式外，不使用 html 语法改变文字样式，仅在特殊情况下使用 html 语法增添文档的趣味性。

:::
