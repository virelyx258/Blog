---
title: "兜兜转转又回到 Astro"
pubDate: "2026-08-03T00:15:00.000Z"
cover: "https://image.luming.cool/i/2026/08/02/6a6f64cdd1ad5.webp"
categories: ['生活']
tags: ['博客系统','Astro']
draft: false
comments: true
---

这不算正式文章，算一篇碎碎念。

以前我用过 WordPress、Typecho，但是服务器架设在海外，就算用上 CDN，也掩盖不了海外线路先天的延迟劣势。再加上 PHP 系统每次请求都需要重新执行一次程序，导致延迟会进一步升高。

我中途换过 Astro 静态系统，我如是说，速度确实很快。它几乎能跑满服务器的速度上限。但是有一个问题——这上面没有我喜欢的主题。我用过 Fuwari，但它动画太多了，且 UI 戳不中我的心。这导致我后来为了一个喜欢的主题 Mirages，弃用了 Astro，重新安装了 Typecho。

暑假了，本着对极致速度的执念，我打开 OpenCode CLI，开始将 Mirages 移植至 Astro。

我选择了更快更新的 TailWind CSS 作为首要技术栈，但是如果这样，就不能 100% 复刻原主题的样式了。我的想法是，看起来像就可以。于是我就坚持下来，完成了 Astro 版 Mirages 主题。

全程使用 GPT 5.6 Sol、Terra、Luna 模型。前前后后提了近百次意见，消耗的成本大概有 ￥50。

你现在看到的就是本站的 Astro 版本。原 Typecho 站点的所有数据（包含评论）均已迁移至 Astro 系统。尽情享受新版博客的速度吧！
