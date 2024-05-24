# 自定义导航栏

## HTML

如果你需要定制导航栏，可以用 HTML 创建一个导航栏。

!> 注意：文档的链接都要以 `#/` 开头。

```html
<!-- index.html -->

<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">中文</a>
  </nav>
  <div id="app"></div>
</body>
```

## Markdown

那我们可以通过 Markdown 文件来配置导航。首先配置 `loadNavbar`，默认加载的文件为 `_navbar.md`。具体配置规则见[配置项#loadNavbar](configuration.md#loadnavbar)。

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true,
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
```

```markdown
<!-- _navbar.md -->

- [En](/)
- [chinese](/zh-cn/)
```

!> 你需要在 `./docs` 目录下创建一个 `.nojekyll` 文件，以防止 GitHub Pages 忽略下划线开头的文件。

`_navbar.md` 加载逻辑和 `sidebar` 文件一致，从每层目录下获取。例如当前路由为 `/zh-cn/custom-navbar` 那么是从 `/zh-cn/_navbar.md` 获取导航栏。 如果当前目录没有 `_navbar.md`，它将返回父目录。 如果导航内容过多，可以写成嵌套的列表，会被渲染成下拉列表的形式。

## 嵌套

您可以通过缩进在某个父级下的项目来创建子列表。

```markdown
<!-- _navbar.md -->

- Getting started

  - [Quick start](quickstart.md)
  - [Writing more pages](more-pages.md)
  - [Custom navbar](custom-navbar.md)
  - [Cover page](cover.md)

- Configuration
  - [Configuration](configuration.md)
  - [Themes](themes.md)
  - [Using plugins](plugins.md)
  - [Markdown configuration](markdown.md)
  - [Language highlight](language-highlight.md)
```

渲染为

![嵌套导航栏](../_images/zh-cn/nested-navbar.png "嵌套导航栏")

## 整合自定义导航栏与 emoji 插件

如果你使用 [emoji 插件](plugins#emoji):

```html
<!-- index.html -->

<script>
  window.$docsify = {
    // ...
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/emoji.min.js"></script>
```

例如，你可以在自定义导航栏 Markdown 文件中使用旗帜表情：

```markdown
<!-- _navbar.md -->

- [:us:, :uk:](/)
- [:cn:](/zh-cn/)
```
