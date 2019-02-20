---
title: LTR1.0-hexo
categories:
  - 前端研发
tags:
  - 开源协作
date: 2019-02-19 22:57:27
description: 基于 "Hexo" 构建技术博客 "Leander's codebook" 将采用 "LTR1.0-hexo" 排版规则撰写文章。此排版规则会不定期更新，根据行文风格和标准约束构建易读、友好的文档规范。
---

# 编写规范

  `LTR1.0(Leander typesetting rule)`-hexo，采用标准化文档编写规范构建易于编写、维护、传阅的文档内容。

## 内容构成

  `Leander's codebook`由`pages`和`post`两种模板构成。

- `pages`为精排文章，系基于确定主题，仔细考证、严谨论述的文章，这类文章使用`tag`标记归档。
- `post`为一般文帖，是保证频率更新的技术帖子。这些帖子不以系统性地组织，排版也不会进行总体设计，使用`category`栏目、`tag`标记进行归档。

## 排版规范

- `title`标记采用1-3级梯度组织行文，以下正文级题序采用`列表`标记组织
- `icon`素材库来自：<https://fontawesome.com/v4.7.0/icons/>
- `摘要`&`引言`：文档`description`摘要、章`excerpt`引言是必要的最低要求
- `留空`：`markdownlint`基础上，中英文单词间留1空，`列表`行末使用2空
- `词汇`：中英文专业性词汇应采取官方表述，避免缺乏严谨性的网络词汇、不确定性的生活习语
- `通用排版规范`，遵循 `markdownlint` 自检，应用 [`han.js`](https://github.com/theme-next/theme-next-han) 优化中文排版

## 文档组件

1. `quote` 引用

```htt
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```

{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
2. `code block`代码块

优先使用 `markdown code block` 来获得充分的标准兼容，当代码块较复杂时可以使用 `hexo` 代码块标签实现更强大的代码块示例。

- `markdown code block`，使用三个一组闭合`反引号`创建默认样式代码块

- `hexo` 代码块标签，创建包含类型、链接、文件名的完整代码示例

```text
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```

{% codeblock hexo模板标签 https://hexo.bootcss.com/ 类型标题外链示例.snippet %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
3. `pdf preview`：本博客集成了pdf预览组组件，通过如下代码集成预览下载

- pdf组件

```htt
{% pdf https://pdfurl %}
```

- 下载pdf

```htt
{% pdf http://7xov2f.com1.z0.glb.clouddn.com/bash_freshman.pdf %}
本地连接：
{% pdf ./pdf名字.pdf %}
```

# 文风要求

- 简练至上
- 充分考究
- 内因外援
- 渐进提高

# 维护规约

# 传播分发
