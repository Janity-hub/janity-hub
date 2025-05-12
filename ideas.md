#Ideas and Todo:

## 设置网页自动引用writing和artwork：

markdown-articles/               ← 专门写作用
├── ai/
│   ├── 2024-llm-apps.md
├── devops/
│   ├── docker-tips.md
├── life/
│   ├── emotions-vs-value.md

your-site/
├── content/
│   └── posts/
│       └── articles/           ← 作为子模块引用 markdown-articles
├── config.yaml
├── static/
- writing-portfolio/：把文章按分类放进去，比如 ai/、devops/、life/
- 文章放到文件夹之后，Hugo 网页链接结构会变化，但只需要设置好 front matter 或 config
统一在 config.yaml 中设置 slug 或 permalink 规则

```yaml
permalinks:
  posts: /:slug/
```

然后每篇文章用 slug 控制网址名即可，避免因文件夹结构变动而改链接。

- writing库内部结构设置
把文章放进子目录，再保留简洁首页结构：
writing-portfolio/
├── README.md             ← 仍然显示在主页顶部
├── articles/
│   ├── 2024-05-ai-chatbot.md
│   ├── 2024-05-cloud-troubles.md
├── archive/
│   └── 2023-xx-...md

- 平面设计自动添加到个人网页
发在 GitHub，再同步到网站
把设计图放在 artwork/ 文件夹
Hugo 通过 static/artwork/xxx.jpg 引用，或者用 Markdown 插入图像展示
可以做一个作品展示页 /artwork/，自动列出所有作品图
图片自动加载需要放到 static/ 或 content/posts/xxx/index.md 同目录下

## 网页中添加简历和home

## 能力模块展示

| 能力模块           | 实际做了什么                                       | 如何展示（简历 / 网站 / LinkedIn）                                                       |
| -------------- | --------------------------------------------- | ------------------------------------------------------------------------------ |
| **GitHub结构理解** | 建多个仓库 + 分类文章 + README 编排 + 子模块引用              | 在简历中写：`熟悉 GitHub 仓库结构设计与版本管理（多仓库内容管理 + 子模块协同）`，附上链接指向你的 `writing-portfolio` 仓库 |
| **项目操作经验**     | 用 Stack 主题做网站、结构调整首页导航、调 front matter、处理构建bug | 在项目描述中写：`独立搭建个人网站，使用 Hugo + GitHub Pages，完成主题配置、自定义样式、首页导航与部署脚本编排`，贴你的个人网址     |
| **系统设计意识**     | 内容按分类整理、命名清晰、结构跨平台同步（写作→网站→Medium→GitHub）     | 在个人简介或博客介绍页写：“构建跨平台内容系统，涵盖 Markdown 写作 → Hugo 发布 → GitHub 内容归档 → 多平台分发”        |

## 写文展示魔改stack主题

可以写的内容模块包括：

遇到的难题：主题结构复杂，联动难配置，URL 路由乱

我是怎么逐步理解并修改的（配图展示）

最终成果：多平台联动，仓库同步，自动展示，美观一致

我的建议/经验总结


> 仓库联动 + 魔改主题 + 全站结构优化：

内容与展示系统解耦（文章写在一个库，网页是另一个）

多内容源联动展示（设计作品、项目、博客）

结构级魔改（改 front matter、菜单分类、slug链接、主题布局）

## AI应用制作：

- Dify接入AI大模型，自定义AI Bot
设计：

独特的Prompt逻辑结构（多步、角色设定、输出格式）

明确的用途（如简历优化、情绪梳理、API接入说明）

前端接入页面 or 与网站联动

- Cursor 做 Prompt工程、代码生成、自动测试等“编程环节优化”
辅助开发AI项目

## Stable Diffusion提示词，做Design板块

- 视觉+技术结合展示项：
学提示词 + 生图	发博客介绍提示词设计思路，附生成图（作品）
比较不同提示词差异 + 效果图	形成“Prompt设计视觉指南”
做成设计集 / AI视觉实验	放在 design 板块，变成“生成式视觉项目”
加个Tagline或项目说明	懂AI懂审美，还能结构化表达

- 初步可以先用几个免费在线平台跑图：

https://playgroundai.com/

https://clipdrop.co/stable-diffusion

https://www.artbreeder.com/（风格混合类）

# 目标汇总

| 方向          | 意图                   |
| ----------- | -------------------- |
| 日语          | 长线语言技能、N2考试、生活/作品表达用 |
| DevOps      | 核心技术方向、长期饭碗          |
| GitHub      | 搭建内容中心、展示技能、版本管理     |
| 网站          | 搭好内容前台，构建身份和展示入口     |
| API         | AI工具尝试、拓展技术视野、未来可复用  |
| Stable Diff | 设计板块补充内容、作品集素材       |

