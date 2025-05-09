# 快速开始

推荐全局安装 `docsify-cli` 工具，可以方便地创建及在本地预览生成的文档。

```bash
npm i docsify-cli -g
```

## 初始化项目

如果想在项目的 `./docs` 目录里写文档，直接通过 `init` 初始化项目。

```bash
docsify init ./docs
```

## 写入内容

在 `init` 完成后，你可以看到 `./docs` 子目录中的文件列表。

- `index.html` 入口文件
- `README.md` 会做为主页内容渲染
- `.nojekyll` 用于阻止 GitHub Pages 忽略掉下划线开头的文件

直接编辑 `docs/README.md` 就能更新文档内容，当然也可以[添加更多页面](zh-cn/adding-pages)。

## 本地预览

使用 `docsify serve` 运行本地服务器。 你可以在 `http://localhost:3000` 上预览你的网站。

```bash
docsify serve docs
```

?> 更多命令行工具用法，参考 [docsify-cli 文档](https://github.com/docsifyjs/docsify-cli)。

## 手动初始化

下载或使用以下代码创建一个 `index.html` 模板：

<div id="template">

<a href="#" class="button primary" download="index.html">下载模板</a>

<!-- prettier-ignore -->

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">

    <!-- Core Theme -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/themes/core.min.css">
  </head>
  <body class="loading">
    <div id="app"></div>

    <!-- Configuration -->
    <script>
      window.$docsify = {
        //...
      };
    </script>

    <!-- Docsify.js -->
    <script src="//cdn.jsdelivr.net/npm/docsify@5"></script>

    <!-- Plugins (optional) -->
    <!-- <script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/search.min.js"></script> -->
  </body>
</html>
```

</div>

### 指定 docsify 版本

?> 注意：在下面两个例子中，当 docsify 发布新的主要版本时，需要手动更新 docsify URL（例如，`v5.x.x` => `v6.x.x`）。 定期检查 docsify 网站，以查看新的主要版本是否已发布。

在 URL 中指定一个主要版本 (`@5`)，可使你的网站自动接收非破坏性增强（即 "minor" 更新）和错误修复（即 "patch" 更新）。 这是加载 docsify 资源的推荐方式。

<!-- prettier-ignore -->

```html
<!-- Core Theme -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/themes/core.min.css">

<!-- Docsify -->
<script src="//cdn.jsdelivr.net/npm/docsify@5"></script>
```

如果你希望将 docsify 锁定到特定版本，请在 URL 中的 `@` 符号后指定完整版本。 这是最安全的方法，可确保无论 docsify 的未来版本如何更改，你的网站都将以相同的方式显示和运行。

<!-- prettier-ignore -->

```html
<!-- Core Theme -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5.0.0/themes/core.min.css">

<!-- Docsify -->
<script src="//cdn.jsdelivr.net/npm/docsify@5.0.0"></script>
```

### 手动预览你的网站

如果你的系统里安装了 Python 的话，也可以很容易地启动一个静态服务器去预览你的网站。

```python
# Python 2
cd docs && python -m SimpleHTTPServer 3000
```

```python
# Python 3
cd docs && python -m http.server 3000
```

## Loading 提示

如果你想要，你可以在 docsify 开始渲染文档之前显示一个加载提示信息：

```html
<!-- index.html -->

<div id="app">Please wait...</div>
```

如果更改了 `el` 的配置，需要将该元素加上 `data-app` 属性：

```html
<!-- index.html -->

<div data-app id="main">Please wait...</div>

<script>
  window.$docsify = {
    el: '#main',
  };
</script>
```

对比 [el 设置](zh-cn/configuration#el)。

<script>
  (function() {
    const linkElm = document.querySelector('#template a[download="index.html"]');
    const codeElm = document.querySelector('#template code');
    const html = codeElm?.textContent;

    linkElm?.setAttribute('href', `data:text/plain,${html}`);
  })();
</script>
