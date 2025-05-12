# Hugo 子模块展示问题

问题核心：
用了子模块，把 GitHub 仓库挂在了 Hugo 的目录下：

content/insights/ → 对应 writing 仓库

content/design/ → 对应 design 仓库

但网页上却统一展示为默认的 /posts/ 模板内容，而没有按照目录分别展示为“文章”、“设计”等独立内容块。

核心原因：Hugo 默认不会按目录区分布局，而是按内容类型（type）或 section
解决思路（结构+行为两端要一起改）：

## 步骤一：

title = "我的文章"
type = "insights"

## 步骤二：自定义布局（layouts）来控制显示效果

网站可能现在所有列表页都走 layouts/_default/list.html，这会导致不同目录显示一样。

新建两个文件：

layouts/insights/list.html
layouts/design/list.html
每个 list.html 放想要的展示结构，比如只展示 .Summary、只显示 .Params.category 等等。

这样就能做到：不同目录 → 不同展示。

## 步骤四：可选的菜单和导航联动

在 config.toml 里加导航链接：

[[menu.main]]
name = "Insights"
url = "/insights/"
weight = 1

[[menu.main]]
name = "Design"
url = "/design/"
weight = 2

卡的点大概率是以下其中之一：
type 没设置 → Hugo 默认认为你所有内容都是 post，导致走默认模板；
主题 stack 没有根据目录生成自定义布局 → 所有页面走了相同模板；

## layout修改

### 新建一个 layout 文件，不改原来的：

layouts/insights/list.html

内容：
<h1>Hello, this is insights list page.</h1>

```bash
{{ define "main" }}
  <h1>Hello from insights section!</h1>
  <ul>
  {{ range .Pages }}
    <li>{{ .Title }}</li>
  {{ end }}
  </ul>
{{ end }}
```

然后访问 /insights/ 页面，看看是不是这个页面生效了。

type + section 被 Hugo 正确识别；

修改不会影响别的 layout

2. 每次只改一个变量，立刻刷新看结果

3. 在 Git 开一个新分支（比如 layout-test），大胆改：

```bash
git checkout -b layout-test
```

改完之后如果不满意：

```bash
git switch main
git branch -D layout-test
```

> stack 的 layout 有分类功能，它和其他文件有“联动”吗

layouts/_default/ 是所有 section 的通用模板（list.html、single.html）；

layouts/insights/ 是新建的特定 section 模板；

Hugo 会优先读取最具体的那个文件，即：

layouts/insights/list.html > layouts/_default/list.html

所以只要在 layouts/insights/ 写自己的模板，stack 的原始模板不会被影响。
stack 的主题一般把它的所有布局都封装在 themes/stack/layouts/，在项目本地自己建的 layout 会优先覆盖，但并不会修改主题源代码。

# hugo默认打开不是home页

Hugo 的首页默认不是 content/index.md 渲染的

Hugo 的行为是这样的：

默认首页是 layouts/index.html；

content/index.md 并不自动映射为首页；

如果主题（比如 Stack）没单独写首页逻辑，那它就会自动跳到 content/post/ 或其他默认 section 的列表。

所以以为自己“改了首页”，但其实改的是一个完全没被渲染的文件。

## 方案 A：使用 layouts/index.html 控制首页内容

创建文件：
layouts/index.html

内容可以是想渲染的东西，比如调用某个 section、展示卡片组件，最简单可以写：

```bash
{{ define "main" }}
<h1>Welcome to My Site</h1>
<p>This is my homepage.</p>
{{ end }}
```

## 方案 B：Stack 主题提供 homeSections 参数

在 config.toml 添加类似这段：

```bash
[params.home]
  sections = ["insights", "projects", "design"]
  intro = true
  profile = true
```

这控制首页显示哪些 section，用不用简介、用不用头像。

> 注意
如果写错了路径（比如 [params.home] 放到 [menu] 下面），那就完全无效；

如果没有 layouts/index.html，那 Hugo 会 fallback 到 list.html

改一整天没反应，大概率是以下情况之一：
- 改的是 content/index.md → 它压根不控制首页渲染；

- config.toml 写了 params.home，但写错了位置或 key；

- 没有创建 layouts/index.html，而主题没有自定义首页模板 → 回退为文章列表


