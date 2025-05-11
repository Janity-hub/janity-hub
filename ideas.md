#Ideas and Todo:

- 制作有用链接合集

- 设置网页自动引用writing和artwork：
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

- 修改writing README链接

- 网页中添加简历

- 平面设计自动添加到个人网页
发在 GitHub，再同步到网站
把设计图放在 artwork/ 文件夹
Hugo 通过 static/artwork/xxx.jpg 引用，或者用 Markdown 插入图像展示
可以做一个作品展示页 /artwork/，自动列出所有作品图
图片自动加载需要放到 static/ 或 content/posts/xxx/index.md 同目录下

- 能力模块

| 能力模块           | 实际做了什么                                       | 如何展示（简历 / 网站 / LinkedIn）                                                       |
| -------------- | --------------------------------------------- | ------------------------------------------------------------------------------ |
| **GitHub结构理解** | 建多个仓库 + 分类文章 + README 编排 + 子模块引用              | 在简历中写：`熟悉 GitHub 仓库结构设计与版本管理（多仓库内容管理 + 子模块协同）`，附上链接指向你的 `writing-portfolio` 仓库 |
| **项目操作经验**     | 用 Stack 主题做网站、结构调整首页导航、调 front matter、处理构建bug | 在项目描述中写：`独立搭建个人网站，使用 Hugo + GitHub Pages，完成主题配置、自定义样式、首页导航与部署脚本编排`，贴你的个人网址     |
| **系统设计意识**     | 内容按分类整理、命名清晰、结构跨平台同步（写作→网站→Medium→GitHub）     | 在个人简介或博客介绍页写：“构建跨平台内容系统，涵盖 Markdown 写作 → Hugo 发布 → GitHub 内容归档 → 多平台分发”        |

