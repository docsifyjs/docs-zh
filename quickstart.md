# 快速开始

推荐全局安装 `docsify-cli` 工具，可以方便地创建及在本地预览生成的文档。 开始写文档 初始化成功后，可以看到 `./docs` 目录下创建的几个文件 通过运行 `docsify serve` 启动一个本地服务器，可以方便地实时预览效果。默认访问地址 http://localhost:3000 。 _index.html_

```bash
npm i docsify-cli -g
```

## 初始化项目

如果想在项目的 `./docs` 目录里写文档，直接通过 `init` 初始化项目。

```bash
文档化 init ./docs
```

## 写入内容

在`init`完成后，你可以看到`./docs`子目录中的文件列表。

- `index.html` 入口文件
- `README.md` 会做为主页内容渲染
- `.nojekyll` 用于阻止 GitHub Pages 忽略掉下划线开头的文件

直接编辑 `docs/README.md` 就能更新文档内容，当然也可以[添加更多页面](zh-cn/more-pages.md)。

## 本地预览

用 `docsify Serve` 运行本地服务器。 您可以在 `http://localhost:3000` 上预览您的网站。

```bash
对服务文档
```

?> 更多命令行工具用法，参考 [docsify-cli 文档](https://github.com/docsifyjs/docsify-cli)。

## 手动初始化

如果不喜欢 npm 或者觉得安装工具太麻烦，我们可以直接手动创建一个 `index.html` 文件。

```html
<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <meta charset="UTF-8">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css">
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      //...
    }
  </script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
</body>
</html>
```

### 指定文档化版本

?> 注意以下两个示例： 当发布新的主要版本的文档化时，需要手动更新URL(e)。 。`v4.x.x` => `v5.x.x`)。 定期检查文档化网站，以查看新的主要版本是否已发布。

在 URL (`@4`) 中指定一个主要版本将允许您的网站收到非破坏性的增强系统 (i)。 。"少量"更新) 和 bug 修复(例如"补丁"更新) 。 这是建议的加载资源文档化的方式。

```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" />
<script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
```

如果您喜欢锁定文档化为特定的版本，请在URL中的`@`符号之后指定完整版本。 这是确保你的网站以同样的方式看起来和行为的最安全的方式，不管对未来版本的docsify做出了什么更改。

```html
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/docsify@4.11.4/themes/vue.css"
/>
<script src="//cdn.jsdelivr.net/npm/docsify@4.11.4"></script>
```

### 手动预览您的网站

如果你的系统里安装了 Python 的话，也可以很容易地启动一个静态服务器去预览你的网站。

```python2
cd docs && python -m SimpleHTTPServer 3000
```

```python3
cd 文档 && python -m http.server 3000
```

## Loading 提示

如果您想要，您可以在对准开始渲染文档之前显示一个加载对话框：

```html
  <!-- index.html -->

  <div id="app">加载中</div>
```

如果更改了 `el` 的配置，需要将该元素加上 `data-app` 属性。

```html
  <!-- index.html -->
  <div data-app id="main">加载中</div>

  <script>
    window.$docsify = {
      el: '#main'
    }
  </script>
```

对比 [el 设置](zh-cn/configuration.md#el)。
