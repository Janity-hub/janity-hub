# Hugo 项目编辑发布流程（适用于 Stack 主题 + GitHub Pages）

- 已经在本地 git clone 网站项目仓库
- 已经修改页面： 在 content/ 里写 .md 文件，或改首页设置 / 配置文件，图片放在 static/ 或文章同目录下

## 每次发布流程

### 第 1 步：本地预览（看有没有出 bug）

```bash
hugo server -D
```

浏览器打开 http://localhost:1313/，检查页面是否正常。

### 第 2 步：构建静态网页

```bash
hugo
```

这一步会把网页内容生成到 public/ 文件夹里

### 第 3 步：把更改提交到 Git 仓库

```bash
git add .
git commit -m "更新网站内容 + 文章"
git push origin main
```

如果 public/ 作为 GitHub Pages 仓库的分支（比如 gh-pages）：

```bash
cd public
git add .
git commit -m "部署"
git push origin gh-pages
```

## 建一个 deploy.sh 脚本自动化上面步骤：

```bash
#!/bin/bash
echo "构建 Hugo 网站..."
hugo

echo "提交源码..."
git add .
git commit -m "更新源码"
git push origin main

echo "进入 public 部署目录..."
cd public
git add .
git commit -m "部署"
git push origin gh-pages
cd ..
```

