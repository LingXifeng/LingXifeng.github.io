---
title: 用 Hexo + GitHub Pages 搭建免费博客
categories:
  - 技术
tags:
  - Hexo
  - GitHub
  - 博客
abbrlink: 13dd777f
date: 2026-11-09 16:30:00
---

这篇文章记录一下用 Hexo + GitHub Pages 搭建博客的过程，给同样想建博客的朋友参考。

## 为什么选 Hexo + GitHub Pages

| 方案 | 优点 | 缺点 |
|------|------|------|
| Hexo + GitHub Pages | 免费、简单、中文社区好 | 需要 Node.js 环境 |
| Hugo + GitHub Pages | 速度极快、单文件 | 中文主题相对少 |
| Jekyll + GitHub Pages | GitHub 原生支持 | Ruby 环境，速度慢 |

综合考虑，Hexo 是中文开发者最常用的方案。

## 搭建步骤

### 1. 安装 Hexo

```bash
npm install -g hexo-cli
hexo init my-blog
cd my-blog
npm install
```

### 2. 写文章

```bash
hexo new "我的第一篇文章"
```

这会在 `source/_posts/` 下生成一个 Markdown 文件，编辑它即可。

### 3. 部署到 GitHub Pages

把代码推送到 GitHub 仓库，配置 GitHub Actions 自动构建，每次 `git push` 就会自动发布。

## 写新文章的日常流程

```bash
# 1. 新建文章
hexo new "今天学了什么"

# 2. 编辑 source/_posts/今天学了什么.md

# 3. 推送到 GitHub
git add .
git commit -m "新文章：今天学了什么"
git push
```

等 GitHub Actions 跑完，文章就自动上线了。

## 小结

整个方案的核心优势是：**你只需要关注写 Markdown，剩下的全部自动化**。适合不想折腾服务器、只想安静写技术博客的人。
