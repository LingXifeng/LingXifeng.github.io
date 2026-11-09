---
title: 博客进阶功能演示
categories:
  - 技术
tags:
  - Hexo
  - Fluid
  - 教程
sticky: 100
abbrlink: 11c4077c
date: 2026-11-09 19:00:00
---

这篇文章演示新添加的几个功能。注意本篇设置了 `sticky: 100`，所以会固定在首页最前面。

## 1. 文章置顶

在文章的 Front-matter 中加一行 `sticky` 即可：

{% raw %}
```yaml
---
title: 重要文章
sticky: 100    # 数字越大越靠前
---
```
{% endraw %}

本篇文章就设了 `sticky: 100`，所以你在首页看到它排在最前面。适合放：
- 博客使用指南（就像这篇）
- 系列文章导航
- 重要公告

## 2. GitHub Emoji

安装 `hexo-filter-github-emojis` 后，在 Markdown 里直接写 `:emoji名称:` 就能渲染。对技术写作特别方便：

| 写法 | 效果 | 用途 |
|------|------|------|
| `:rocket:` | :rocket: | 新功能、部署成功 |
| `:bug:` | :bug: | bug 修复 |
| `:tada:` | :tada: | 庆祝、首发 |
| `:fire:` | :fire: | 热门、性能 |
| `:memo:` | :memo: | 笔记 |
| `:wrench:` | :wrench: | 配置、工具 |
| `:books:` | :books: | 学习资料 |
| `:warning:` | :warning: | 注意事项 |
| `:checkered_flag:` | :checkered_flag: | 完成、终点 |
| `:construction:` | :construction: | 施工中、WIP |

在文章标题或段落开头用 emoji，比纯文字更生动。比如：

> :rocket: 今天成功把博客部署到了 GitHub Pages！
>
> :bug: 修复了暗黑模式下代码高亮颜色不对的问题。
>
> :books: 推荐几本系统设计的书：《DDIA》、《系统设计面试》。

完整 emoji 列表见：https://github.com/github/gemoji/blob/master/db/emoji.json

## 3. 文章资源文件夹

开启了 `post_asset_folder: true` 后，每篇文章可以有自己的图片文件夹。

**使用方式：**

用 `hexo new "my-post"` 创建文章时，会自动生成：

```
source/_posts/
  ├── my-post.md       ← 文章
  └── my-post/         ← 这篇文章专属的图片文件夹
```

把截图放进 `my-post/` 文件夹后，在文章里直接引用：

```markdown
![截图说明](my-post/screenshot.png)
```

好处是图片跟着文章走——文章删了图片也自动删，不会堆积在全局 `source/img/` 里。

## 4. robots.txt

已自动生成 `robots.txt`，内容如下：

```
User-agent: *
Allow: /
Disallow: /js/
Disallow: /css/
Disallow: /img/
Sitemap: https://lingxifeng.github.io/sitemap.xml
```

这告诉搜索引擎：可以爬所有页面，但不要爬 js/css/img 等静态资源，并指向 sitemap 帮助发现文章。

## 5. HTML/CSS 压缩

生成的 HTML 和 CSS 会自动压缩，去掉多余空格和换行。页面体积更小，加载更快。

## 6. RSS 全文输出

RSS 订阅的 `content_limit` 已从 200 调到 2000，读者在 Feedly / Inoreader 等 RSS 阅读器里能看到几乎完整的文章内容，不用点开网页。

## 7. Giscus 评论（备选）

配置已就绪，使用时只需：
1. 在 GitHub 仓库 Settings → Features 勾选 Discussions
2. 安装 giscus app：https://github.com/apps/giscus/installations/new
3. 在 https://giscus.app 生成 `repo_id` 和 `category_id`，填入 `_config.fluid.yml`
4. 把 `post.comments.type` 从 `gitalk` 改为 `giscus`

比 Gitalk 好在：不需要 Client Secret，评论存在 Discussions 里更整洁，支持反应表情。
