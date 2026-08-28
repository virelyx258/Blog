---
title: "Eidolon 主题短代码演示"
pubDate: "2026-08-12T01:10:32.630Z"
categories: ['科技']
tags: ['主题','Astro']
draft: false
comments: true
webmention: true
---

Eidolon 主题支持短代码。除兼容 [Mirages](https://get233.com/archives/mirages-intro.html) 的全部短代码外，额外增加了“Tools”组件。

善于运用短代码可以使文章内容更丰富。

---

短代码的统一书写形式：

```
[shortcode param="value"]内容[/shortcode]
亦或是
[shortcode param="value"/]
```



直接在 MarkDown 源代码里书写即可，博客构建时会自动将其转换为对应样式。

---

## 链接按钮

短代码名称：`button`

[tabs]
[tab name="说明"]
生成一个按钮样式的超链接。
[/tab]
[tab name="示例代码"]

```
[button href="https://src.luming.cool/riseforever2026/Eidolon"]Eidolon 主题[/button]
```

[/tab]
[tab name="效果" selected]
[button href="https://src.luming.cool/riseforever2026/Eidolon"]Eidolon 主题[/button]
[/tab]
[tab name="参数"]

| 参数名 | 含义           |
| -----: | :------------- |
|   href | 欲跳转到的链接 |
|   内容 | 按钮标题       |

[/tab]
[/tabs]

## 选项卡

短代码名称：`tabs`

[tabs]
[tab name="说明"]
生成一个多标签页的卡片。
[/tab]
[tab name="示例代码"]

```
[tabs]
[tab name="标签页1标题"]
我是标签页1的内容
[/tab]
[tab name="标签页2标题"]
我是标签页2的内容
[/tab]
[tab name="标签页3标题" selected]
我是标签页3的内容
[/tab]
[tab name="标签页4标题"]
我是标签页4的内容
[/tab]
[/tabs]
```

[/tab]
[tab name="效果" selected]
如你所见。
[/tab]
[tab name="参数"]

|   参数名 | 含义               |
| -------: | :----------------- |
|     name | 标签页的名称       |
| selected | 默认选中的标签页   |
|     内容 | 标签页内显示的内容 |

[/tab]
[/tabs]

## 提示框、警告框

短代码名称：`hint`，`tip`

[tabs]
[tab name="说明"]
生成一个提示或警告卡片。
[/tab]
[tab name="示例代码"]

```
[hint]提示内容[/hint]

[hint warn]警告内容[/hint]

[hint type="danger" title="提示标题"]
提示内容
[/hint]
```

[/tab]
[tab name="效果" selected]
[hint]提示内容[/hint]

[hint warn]警告内容[/hint]

[hint type="danger" title="提示标题"]
提示内容
[/hint]
[/tab]
[tab name="参数"]

| 参数名 | 含义                                                         |
| -----: | :----------------------------------------------------------- |
|   type | 提示类型，默认为 `info`，在没有警告标题的情况下，可以直接将提示类型的值写到参数处。可选的提示类型为 `info`，`warning`(同 `warn`), `danger`(同 `error`)，`success` |
|  title | 提示标题                                                     |
|   内容 | 提示内容                                                     |

[/tab]
[/tabs]

## 下载文件

短代码名称：`file`

[tabs]
[tab name="说明"]
生成一个下载文件的卡片。
[/tab]
[tab name="示例代码"]

```
[file url="https://example.com/download.zip"]示例文件名[/file]
```

[/tab]
[tab name="效果" selected]
[file url="https://example.com/download.zip"]示例文件名[/file]
[/tab]
[tab name="参数"]

| 参数名 | 含义           |
| -----: | :------------- |
|   href | 下载文件的链接 |
|   内容 | 文件名         |

[/tab]
[/tabs]

## 标签

短代码名称：`tag`，`label`

[tabs]
[tab name="说明"]
生成一个标签。
[/tab]
[tab name="示例代码"]

```
[tag]默认 Tag[/tag]
[tag type="primary"]文字的颜色[/tag]
[tag type="info"]文字的颜色[/tag]
[tag type="warn"]文字的颜色[/tag]
[tag type="danger"]文字的颜色[/tag]
[tag type="success"]文字的颜色[/tag]

[tag outline]文字的颜色[/tag]
[tag type="primary" outline]文字的颜色[/tag]
[tag type="info" outline]文字的颜色[/tag]
[tag type="warn" outline]文字的颜色[/tag]
[tag type="danger" outline]文字的颜色[/tag]
[tag type="success" outline="1"]文字的颜色[/tag]
```

[/tab]
[tab name="效果" selected]
[tag]默认 Tag[/tag]
[tag type="primary"]文字的颜色[/tag]
[tag type="info"]文字的颜色[/tag]
[tag type="warn"]文字的颜色[/tag]
[tag type="danger"]文字的颜色[/tag]
[tag type="success"]文字的颜色[/tag]

[tag outline]文字的颜色[/tag]
[tag type="primary" outline]文字的颜色[/tag]
[tag type="info" outline]文字的颜色[/tag]
[tag type="warn" outline]文字的颜色[/tag]
[tag type="danger" outline]文字的颜色[/tag]
[tag type="success" outline="1"]文字的颜色[/tag]
[/tab]
[tab name="参数"]

|  参数名 | 含义                                                         |
| ------: | :----------------------------------------------------------- |
|    type | 默认为 `default`，可选值为 `info`，`warning`(同 `warn`), `danger`(同 `error`)，`success`，`primary`， `default` |
| outline | 是否使用 outline 样式的标签                                  |
|    内容 | 标签展示的文字                                               |

[/tab]
[/tabs]

## 快速输入警告符:  [!/]

短代码名称：`!`

[tabs]
[tab name="说明"]
快速输入:  [!/]
[/tab]
[tab name="示例代码"]

```
[!/]
```

[/tab]
[tab name="效果" selected]
[!/]
[/tab]
[/tabs]

## 折叠框

短代码名称：`collapse`

[tabs]
[tab name="说明"]
可以点击标题展开 / 折叠的内容。
[/tab]
[tab name="示例代码"]

```
[collapse title="标题"]
折叠内容
[/collapse]
```

[/tab]
[tab name="效果" selected]
[collapse title="标题"]
折叠内容
[/collapse]
[/tab]
[tab name="参数"]

| 参数名 | 含义       |
| -----: | :--------- |
|  title | 折叠框标题 |
|   内容 | 折叠框内容 |

[/tab]
[/tabs]

## GitHub

短代码名称：`github`

[tabs]
[tab name="说明"]
放置一个 Github 仓库控件。
[/tab]
[tab name="示例代码"]

```
[github repo="virelyx258/Astro-Theme-Eidolon" /]
```

[/tab]
[tab name="效果" selected]
[github repo="virelyx258/Astro-Theme-Eidolon" /]
[/tab]
[tab name="参数"]

| 参数名 | 含义                                             |
| -----: | :----------------------------------------------- |
|   repo | Github 仓库所属用户及仓库名。格式：用户名/仓库名 |

[/tab]
[/tabs]

## 工具列表

短代码名称：`tools`

[tabs]
[tab name="说明"]
放置一个工具列表卡片。
[/tab]
[tab name="示例代码"]

```
[tools title = "设计"]
[Canva](https://www.canva.cn)+(https://image.luming.cool/i/2026/08/07/6a75ba231df9b.webp)/(图像设计)
[即时设计](https://js.design)+(https://image.luming.cool/i/2026/08/07/6a75c0b9bbf29.webp)/(UI 设计)
[Microsoft 365](https://m365.cloud.microsoft/)+(https://image.luming.cool/i/2026/08/07/6a75bd0318e8e.webp)/(文档处理)
[剪映](https://www.capcut.cn/)+(https://image.luming.cool/i/2026/08/07/6a75bf6a337d1.webp)/(视频剪辑)
[/tools]
```

[/tab]
[tab name="效果" selected]
[tools title = "设计"]
[Canva](https://www.canva.cn)+(https://image.luming.cool/i/2026/08/07/6a75ba231df9b.webp)/(图像设计)
[即时设计](https://js.design)+(https://image.luming.cool/i/2026/08/07/6a75c0b9bbf29.webp)/(UI 设计)
[Microsoft 365](https://m365.cloud.microsoft/)+(https://image.luming.cool/i/2026/08/07/6a75bd0318e8e.webp)/(文档处理)
[剪映](https://www.capcut.cn/)+(https://image.luming.cool/i/2026/08/07/6a75bf6a337d1.webp)/(视频剪辑)
[/tools]
[/tab]
[tab name="参数"]

| 参数名 | 含义       |
| -----: | :--------- |
|  title | 工具集名称 |

[/tab]
[/tabs]