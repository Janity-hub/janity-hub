# Git 储存过一个发布版本 → 网页崩了 → 想回退旧版本怎么做？

## 方法一：Git 命令行回退到某一次 commit

打开本地项目文件夹的 Git 仓库

输入命令查看历史版本：

```bash
git log --oneline
```

会看到类似这样：
f3d91a2 fixed home page crash
4a2b933 added theme
0f9b1a0 initial website deploy
找到想回退到的那个 commit 值（比如 4a2b933）

回退到该版本（会保留历史）：
git checkout 4a2b933
如果只是想看看历史文件，不想覆盖当前，可以加 --detach 参数。

想恢复成当前版本：

```bash
git checkout main
```

或者

```bash
git switch main
```

## 方法二：GitHub 网页回退查看 + 手动恢复

打开 GitHub 仓库 → 点上方菜单里的 “Commits”

找到想恢复的 commit，点进去 → 右上角 “Browse files”

它会展示当时的项目全貌 → 可以复制文件内容粘贴回来，或下载整个版本作为恢复用

