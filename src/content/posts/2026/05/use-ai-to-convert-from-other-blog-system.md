---
cover: "https://image.luming.cool/i/2026/08/03/6a6f79f6a3c44.webp"
title: "使用 AI 从任意博客系统迁移到 Typecho"
pubDate: "2026-05-16T12:40:00.000Z"
updatedDate: "2026-07-14T15:26:50.000Z"
categories:
  - "科技"
tags:
  - "WordPress"
  - "Astro"
  - "Typecho"
comments: true
---


## 前言

去年 9 月，我把自用的博客系统由 WordPress [换到了 Astro](https://www.luming.cool/posts/2025/10/change-domain-3rd)。

从动态博客到静态博客，数据的迁移是一项很大的工程。当时，我是**纯手工迁移**，把 WordPress 博客上的一篇篇文章复制、一张张图片另存。

其实这还没什么，关键是每个文章文件（.md）的 Frontmatter 都需要我手动填写。为了完成这个操作，我马不停蹄地复制了四五个小时。

静态博客用了将近 10 个月了，出于**喜新厌旧**的心理，我重新在服务器上安装了 Typecho，并打算回归动态博客。

这一次，我难道还要手动迁移吗？不了，我会用 AI 了。

## 原理介绍

如今，各大 AI IDE（如 Cursor、TRAE）都具备了一定的 Agent 能力，能操作电脑上的文件。所以，我们可以指挥 AI 从 Astro 博客的根目录读取博客内容（文章、页面、媒体），从 Twikoo 评论系统的数据库读取评论内容，然后将它们融合成一个 Typecho .DAT 备份文件，导入 Typecho 以实现数据迁移。

本文使用的 AI IDE 是 Cursor。

## 开始操作

Typecho 博客文章的一些字段（比如头图 url）是由使用的主题决定的，因此，不同主题下的 .DAT 文件结构是不一样的。

所以在迁移之前，我们需要确保应用了自己想要的主题，且博客内创建了一些测试文章、测试页面以供 AI 理解相应字段。以我用的主题 Mirages 为例，在后台创建几篇文章，并为文章随便设置头图。

![网站外观设置](https://image.luming.cool/i/2026/07/14/6a56545247b55.webp)

![自定义字段](https://image.luming.cool/i/2026/07/14/6a56545135aa1.webp)

之后前往控制台 → 备份 → 开始备份，浏览器会自动开始下载 .DAT 文件。

## 让 AI 熟悉备份文件结构

下载好备份文件后，新建一个空白文件夹，除了把备份文件丢进去以外，再往里面放入我制作的`SKILL.md`，然后用 Cursor 打开该文件夹。

[file url="https://res.luming.cool/d/OneDrive/AI%20Skills/Typecho%20Backup%20Migration%20Skill/SKILL.md?sign=Mn7VFpnQqI8PWdeHU0cmL2FaVYIq53yEuqLyMGAjFqk=:0"]SKILL.md[/file]

对 Cursor 说：

```plaintext
$文件名称$ 是一个 Typecho 博客备份文件，请你根据 SKILL.md 介绍的方法，熟悉一下这个备份文件的结构、字段，稍后我会让你对这个备份文件进行修改。
```

然后稍等片刻，Cursor 就能轻松解析你的 .DAT 文件。

![AI对话](https://image.luming.cool/i/2026/07/14/6a565452bdfac.webp)

## 准备待迁移数据

以 Astro+Twikoo 为例，我将 Astro 项目目录下包含文章的文件夹和 Twikoo 文件夹复制到迁移目录里，并对 Cursor 说：

```plaintext
$Astro 目录$ 目录是我 Astro 博客的数据文件夹，包含我的文章、页面和媒体；
$Twikoo 目录$ 目录里是我博客使用的 Twikoo 评论系统的数据库文件，评论对应的 url 和 Astro 博客里的文章目录名一一对应。
请你先读取 Astro 博客信息及 Twikoo 评论信息，然后完整输出。
```

![image.png](https://image.luming.cool/i/2026/07/14/6a5654534ebf0.webp)

待它读取完毕后，我们检查一下读取出来的信息和实际情况是否相符。如果无误，就着手准备下一步。

## 上传媒体到兰空图床

由于 Astro 博客的媒体文件是和文章存放在一起的，随博客统一部署上线。在迁移至 Typecho 后，我们需要一个平台来存储文章里的媒体。这里使用 [Lsky Pro](https://lsky.pro) 做演示，当然，如果你有自己的图片托管方案，就可以直接跳过本段。

首先你需要有一个现成的 Lsky Pro 实例。我这里就用我自己的图床 [https://image.luming.cool](https://image.luming.cool) 作为演示。

使用 [Apifox](https://apifox.com/)，向 /api/v1/tokens 发送 POST 请求，请求参数如下：


| 字段          | 类型   | 说明 |
| --------------- | -------- | ------ |
| ***email**    | String | 邮箱 |
| ***password** | String | 密码 |

请求后，系统会返回密钥，密钥格式是“Bearer xxxxxxxxx...”，只复制这一段即可。

接着对 Cursor 说：

```plaintext
接下来我需要你把我博客里的媒体上传到 Lsky Pro，并在引用它们的地方进行url替换。
我的 Lsky Pro 地址是 https://example.com/
我的 Token 是 Bearer xxxxxxxxxxx...
```

这样，Cursor 就会完成媒体的上传和本地文章引用地址的替换。

## 开始迁移

文章、页面、媒体都准备就绪后，我们就可以开始生成 DAT 备份文件了。

直接对 Cursor 说：

```plaintext
开始 DAT 文件转换
```

大约 1~2 分钟，它就会将 Astro 博客的数据转换为 Typecho 备份文件。

![开始 DAT 文件转换](https://image.luming.cool/i/2026/07/14/6a5655207fa2c.webp)

![文件](https://image.luming.cool/i/2026/07/14/6a5654515db56.webp)

## 恢复数据

进入 Typecho 后台，控制台 → 备份 → 上传 → 选择文件，选择 Cursor 输出的备份文件，点击“确认恢复”，系统会询问“恢复操作将清除所有现有数据, 是否继续?”，点击“确定”，稍等片刻，即可完成恢复。

恢复完成后，就可以在新的 Typecho 博客里看到我们以前的数据了。Enjoy it!

## 后记

我编写的 SKILL.md 理论上也支持 WordPress 博客数据的转换，只需要把 wp_content 目录放在 Cursor 操作目录下，然后和它说“帮我转换 WordPress 博客的数据”，就能完成转换操作。

AI 在这类重复性工作上的效率太高了，而且它们不会感到累。合理利用它，就能节省大量的时间。

这篇文章的逻辑比较强，读起来可能会有点累。我希望它清晰到了能帮上忙的程度。
