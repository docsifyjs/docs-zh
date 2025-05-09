# 自定义导航栏

## HTML

如果你需要定制导航栏，可以用 HTML 创建一个导航栏。

!> 注意：文档的链接都要以 `#/` 开头。

```html
<!-- index.html -->

<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">简体中文</a>
  </nav>
  <div id="app"></div>
</body>
```

## Markdown

或者，你也可以将 `loadNavbar` 设置为 **true**，并创建 `_navbar.md`，从而创建基于 markdown 的自定义导航文件。比较 [loadNavbar configuration](zh-cn/configuration#loadnavbar)。

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
- [简体中文](/zh-cn/)
```

要创建下拉菜单：

```markdown
<!-- _navbar.md -->

- Translations

  - [En](/)
  - [简体中文](/zh-cn/)
```

!> 你需要在 `./docs` 目录下创建一个 `.nojekyll` 文件，以防止 GitHub Pages 忽略下划线开头的文件。

`_navbar.md` 会从每一级目录加载。 如果当前目录中没有 `_navbar.md`，则会返回上一级目录。 例如，如果当前路径是 `/guide/quick-start`，则将从 `/guide/_navbar.md` 加载 `_navbar.md`。

## 嵌套

你可以通过缩进在某个父级下的项目来创建子列表。

```markdown
<!-- _navbar.md -->

- 入门

  - [快速开始](zh-cn/quickstart.md)
  - [多页文档](zh-cn/more-pages.md)
  - [定制导航栏](zh-cn/custom-navbar.md)
  - [封面](zh-cn/cover.md)


- 配置
  - [配置项](zh-cn/configuration.md)
  - [主题](zh-cn/themes.md)
  - [使用插件](zh-cn/plugins.md)
  - [Markdown 配置](zh-cn/markdown.md)
  - [代码高亮](zh-cn/language-highlight.md)
```

效果图

![嵌套导航栏](../_images/zh-cn/nested-navbar.png "嵌套导航栏")

## 整合自定义导航栏与 emoji 插件

如果你使用 [emoji 插件](zh-cn/plugins#emoji)：

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
