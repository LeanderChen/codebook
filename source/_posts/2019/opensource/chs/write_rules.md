---
title: LTR1.0-hexo
layout: post
categories:
  - opensource
tags:
  - opensource
  - teamwork
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

- title 标记采用1-3级梯度组织行文，以下正文级题序采用`列表`标记组织
- icon 素材库来自：<https://fontawesome.com/v4.7.0/icons/>
- 摘要 & 引言：文档`description`摘要、章`excerpt`引言是必要的最低要求
- 留空：`markdownlint`基础上，中英文单词间留1空，`列表`、`标题`及`文段`行末使用2空
- 通用排版规范。遵循 `markdownlint` 自检，应用 [`han.js`](https://github.com/theme-next/theme-next-han) 优化中文排版

## 命名规范

- 标题：
  - 文章标题为表论属性、专业性，不可使用疑问、反问、反诘等不确定语气
  - 章节标题应简单明了，准确表单组成结构或内容属性
  - 文件标题均采用英文命名，`-`短横标记用于连词单词，`_`标记用于单词连接
  - 栏目标题应参见`scaffolds`脚手架声明列表，不可随意增改划定栏目，不发布明显超出栏目范围的内容
  - 关键词标题同栏目标题
- 引用词汇：中英文专业性词汇应采取官方表述，避免缺乏严谨性的网络词汇、不确定性的生活习语

## 文档组件

1. **quote 引用**  

```swig
<!-- 普通引用 -->
{% blockquote [author[, source]] [link] [source_link_title] %}
content
{% endblockquote %}

<!-- 居中引用 -->
{% centerquote %}
blah blah blah
{% endcenterquote %}
```

{% blockquote David Levithan, Wide Awake https://leanderchen.github.io/codebook leander's codebook %}  
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.  
{% endblockquote %}  

{% centerquote %}  
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.  
{% endcenterquote %}  
2. **note 标注**  

```swig
<!-- 来自bootstrap设计，支持类型：default、primary、success、info、warning、danger -->
{% note class_name %}
Content (md partial supported)
{% endnote %}
```

{% note default %}  
default 类，用于段内参考引用  
{% endnote %}  
{% note primary %}  
primary 类，用于不确定、待验证标记  
[ ] item1  
[ ] item2  
{% endnote %}  
{% note success %}  
success 类，用于已确认、已完成标记  
[x] item1  
[x] item2  
{% endnote %}  
{% note info %}  
info 类，用于一般性标记、补充说明  
{% endnote %}  
{% note warning %}  
warning 类，用于警示、提醒、注意说明  
{% endnote %}  
{% note danger %}  
danger 类，用于禁止、废弃、危险标记  
[!] item1  
[!] item2  
{% endnote %}  

特别地，我们使用 `no-icon` 标记贴注文章的参考引用内容。
{% note no-icon %}  
参考引用：  
1 title. date. [source]  
2 title. date. [source]  
{% endnote %}  
2. **code block 代码块**  

优先使用 `markdown code block` 来获得充分的标准兼容，当代码块较复杂时可以使用 `hexo` 代码块标签实现更强大的代码块示例。

- `markdown code block`，使用三个一组闭合`反引号`创建默认样式代码块

- `hexo` 代码块标签，创建包含类型、链接、文件名的完整代码示例

```swig
<!-- use inpage code-blok -->
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}

<!-- use out code-block -->
{% include_code [title] [lang:language] path/to/file %}

<!-- 引用代码片段 -->
{% iframe url [width] [height] %}
```

{% include_code hello_word lang:text test/hello_world.txt %}

{% codeblock hexo模板标签 https://leanderchen.github.io/codebook/2019/opensource/chs/write_rules.html codeblock_demo.snippet %}  
_.compact([0, 1, false, 2, '', 3]);  
=> [1, 2, 3]  
{% endcodeblock %}  
3. **pdf preview**  
本博客集成了pdf预览组组件，通过如下代码集成预览下载。  

- pdf组件

```swig
{% pdf https://leanderchen.github.io/codebook/downloads/demo/blank_pdf.pdf %}
```

{% pdf https://leanderchen.github.io/codebook/downloads/demo/blank_pdf.pdf %}  
***注： 除有其他固定平台托管的文档，应该引入到项目文件中。***  
4. **media**  

- 图片内容

优先使用Hexo默认语法，当对图片尺寸需加以限定时使用`swig img`标签，该图片将会被索引显示在列表页。

  `Hexo` 的 `swig` 语法标签

```swig
{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```

  `markdown` 原生插入图片

```markdown
(alt_text)[/path/to/image]
```

- 视频内容

```swig
<!-- youtube video -->
{% youtube video_id %}
```

- 外部链接

```mixed
<!-- use markdown -->
[alt_text](/path/to/image)
<!-- use swig -->
{% link text url [external] [title] %}
```

- 引用组件

```swig
<!-- 引用文章 -->
{% post_path slug %}
{% post_link slug [title] %}

<!-- 引用iframe -->
{% iframe url [width] [height] %}

<!-- 引用资源：启用post_asset_folder，资源应通过post对应目录索引 -->
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}

<!-- 引用swing标签 -->
{% raw %}
content
{% endraw %}

<!-- 使用数据文件 -->
{% raw %}
<% for (var link in site.data.menu) { %>
  <a href="<%= site.data.menu[link] %>"> <%= link %> </a>
<% } %>
{% endraw %}
```

# 文风要求

- 简练至上
- 充分考究
- 内引外援
- 渐进提高

# 维护规约

## 编写组

codebook 的编写成员将来自 `codebook项目运营组`， 小组成员来自外部吸纳与内部推荐， 并且将开源社区作为重要的组成来源。

## 社区贡献

您可以通过如下方式向 codebook 项目贡献：

- 修订文章内容，PR修正或文章
- RSS订阅，或以其他方式关注、推荐我们的项目
- 将你的意见、文稿或者想法发送至项目组邮箱 [@codebook](mailto:codebook@tchost.cn)

## 开始写作

假设你现在已经准备好开始写作：

1. 拥有可以稳定使用的 `Windows` 、 `Linux` 或 `Mac OS`工作环境  
2. 掌握Markdown语法与现代编辑器（应该支持Git）的使用， 了解 `Git` 、 `node.js` 、 `NPM`  
3. 准备好创作的激情与想法

你应该逐项检查完成如下步骤，以便你可以高效、准确地写作：

1. 检出项目

如果您是未加入官方写作的社区贡献者，你可能需要先fork项目。

```shell
# confirm your accessable repo address, here is official repo address
# clone repo, after enter work-directory
git clone https://github.com/LeanderChen/codebook.git -b hexo-src

# or maybe you will clone with ssh, if you like
```

***注： 这里对fork项目不做更多注解，我想你应该了解使用 `git [command] --help` 来获取使用参照***
2. 安装 `hexo` 程序、 `next` 主题及其的模块依赖  

```shell
# if your international network is not so good, you should try cnpm: https://npm.taobao.org/
# install hexo-cli
npm install hexo -g

# install hexo dependency
cd codebook
npm install

# install next dependency
cd themes/next
npm install
```

***提示：推荐使用 `WebStorm` ，你可以简单快速的使用 `git` 。 你也可以使用 `Visual Studio Code`并安装 `git for [platform]`。***
3. 安装 `hexo-server` 等本地开发工具

```shell
# install node-cli tools for hexo
# hexo-server is userful for local debug
npm install hexo-server --save

# hexo-deploy-git will be used to deploy static site to `github pages`
npm install hexo-deployer-git --save
```

# 传播分发

codebook 的分发形式分为 `community` 社区版本和 `release` 发行版本， 前者以开源写作的形式标记 branch 版本进行社区维护， 而后者则会根据社区反馈筛选优质文章进行汇编、印刷、发售。  
codebook 的分发渠道有且只有：  

- 发布于 Github pages 地址 <https://leanderchen.github.io/codebook> ， 及 `辰鹄博客` 的镜像版本 <https://blog.tchost.cn/codebook> 将以Web文稿形式发布的 `opensource community` 社区版本  
- 发布于 Github 项目 <https://github.com/leanderchen/codebook> 的 `ebook release` 电子文件版本， 授权申明的印刷出版 `publication release` 版本  
- 发布于 Brain Cluster <https://brain.tchost.cn> 的同名电子书版本， 将作为特殊收录的 `special release` Web文稿发行版本

通常我们的更新发布顺序为： `opensource community` &gt; `publication release` &gt; `ebook release` &gt; `sepcial release`。 其中后两项是可选的，以上也是官方认定的全部分发渠道。  
本项目来自开源社区， 也服务于开源社区， 因此您可以免费地以非商用目的查阅、引用、传播内容。  
开源、自由、成长，祝你幸运！