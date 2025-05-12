# API相关笔记

## API应用思路

| 用途                 | 实例                              |
| ------------------ | ------------------------------- |
| Hugo 博客自动翻译        | 写个脚本，API 翻译 Markdown 文件，生成多语言版本 |
| VS Code 接 AI 助理    | 直接在写代码时提问、生成代码块、解释报错            |
| AI 生成文档/摘要         | 将聊天记录自动总结为文章草稿                  |
| AI 重写旧内容           | 旧博客自动润色、摘要生成器                   |
| AI 接入你的网站          | 做一个“AI客服”解答访客问题                 |
| AI 批量写 Markdown 笔记 | 输入关键词，API 帮你生成知识卡片              |

## 做自己的 ChatGPT 问答系统（用 API 实现）

前端用一个网页（HTML + JS 或 React）来展示聊天界面；

后端用一个小服务（比如 Node.js 或 Flask）来接 OpenAI API；

自己设置：

模型（GPT-3.5 / GPT-4 Turbo）

指令（你希望它回答方式如何）

UI 界面风格

是否保存历史对话、定制 prompt 等

## 可以用APIKey配置CodeGPT

1. 注册 OpenAI API 账号
访问： https://platform.openai.com

登录 OpenAI 账号

点击右上角头像 → View API Keys

点 “Create new secret key” → 复制保存

2. 安装 VS Code 插件：CodeGPT
打开 VS Code

左侧点击扩展商店

搜索 CodeGPT

安装由 Daniel San 托管的版本（一般排在最前）

3. 配置 API Key
在 VS Code 中：

Ctrl + Shift + P 打开命令面板（Mac 是 Cmd + Shift + P）

输入 CodeGPT: Set API Key，回车

粘贴刚才复制的 OpenAI API Key

做法流程：
打开 baseof.html，右键问

## 用 API + 脚本读取所有网页文件

写个 Python 脚本，模拟以下操作：

读取整个 Hugo 项目中需要修改的文件（比如 layout、config、conten、 baseof.html + i18n.json）

把它们打包成一段长文本 + 修改需求；

用 OpenAI API 和 prompt 一起发给GPT：“请在 baseof.html 中添加支持中英切换的语言菜单，配置文件见下；语言内容见下”

返回修改后的版本；

程序自动覆盖原文件或输出为副本。

