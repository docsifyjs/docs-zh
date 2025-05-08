# 服务器侧渲染器

!> :construction: SSR support is experimental and incomplete. 我们正在为此而努力。 插件和
一些Docsify功能还不能在 SSR 模式中工作。 :construction:

<!--
This link is dead.
See https://docsify.now.sh
-->

项目地址在 https://github.com/docsifyjs/docsify-ssr-demo

## 什么是 SSR?

- 更好的 SEO
- 更酷的感觉

## 快速开始

如果你熟悉 `now` 的使用，接下来的介绍就很简单了。先创建一个新项目，并安装 `now` 和 `docsify-cli`。

```bash
npm i now docsify-cli -D
```

编辑 `package.json`。假设你的文档放在 `./docs` 子目录。 以下假设文档位于`./docs`子目录中。

```json
{
  "name": "my-project",
  "scripts": {
    "start": "docsify start . -c ssr.config.js",
    "deploy": "now -p"
  },
  "files": [
    "docs"
  ],
  "docsify": {
    "config": {
      "basePath": "https://docsify.js.org/",
      "loadSidebar": true,
      "loadNavbar": true,
      "coverpage": true,
      "name": "docsify"
    }
  }
}
```

!> 其中 `basePath` 相当于 webpack 的 `publicPath` ，为文档所在的路径，可以填你的 docsify 文档网站。我们可以使用本地或者远程文件。 我们可以使用本地或远程文件。

我们可以预览本地网站以查看它是否正常工作。

```bash
npm 启动

# 打开 http://localhost:4000
```

发布！

```bash
现在-p
```

现在，您支持SSR。

## 定制模板

你可以提供一个整页模板，例如：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>docsify</title>
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css" title="vue">
</head>
<body>
  <!--inject-app-->
  <!--inject-config-->
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs/components/prism-bash.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs/components/prism-markdown.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs/components/prism-nginx.min.js"></script>
</body>
</html>
```

模板应包含这些评论以提供应用内容。

- `<!--inject-app-->`
- `<!--inject-config-->`

## 配置

配置可以单独写在配置文件内，然后通过 `--config config.js` 加载，或者写在 `package.json` 中。

```js
module.exports = {
  template: './ssr.html',
  maxAge: 60 * 60 * 1000, // lru-cache 设置
  config: {
   // docsify 设置
  }
}
```

## 为您的 VPS 部署

你可以直接在你的 Node 服务器上执行 `docsify start` 。

```js
var Renderer = require('docsify-server-render')
var readFileSync = require('fs').readFileSync

// init
var renderer = new Render(*
  template: readFileSync('./docs/index.template. tml', 'utf-8'),
  config: @un.org,
    name: 'docsify',
    仓库: 'docsifyjs/docsify'
  }
})

渲染器。 enderToString(url)
  .then(html => {})
  .catch(err => {})
```
