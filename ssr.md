# 服务端渲染（SSR）

项目地址: https://github.com/docsifyjs/docsify-ssr-demo

!> SSR的支持是实验性质的， 还没完成，主要是因为一些插件和特性在SSR模式中仍不能正常工作，我们正在努力实现中。 


## 什么是 SSR?
- 更好的 SEO
- 更酷的感觉


## 快速开始

如果你熟悉 `now` 的使用，接下来的介绍就很简单了。先创建一个新项目，并安装 `now` 和 `docsify-cli`。

```bash
npm i now docsify-cli -D
```

编辑 `package.json`。假设你的文档放在 `./docs` 子目录。

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

!> 其中 `basePath` 相当于 webpack 的 `publicPath` ，为文档所在的路径，可以填你的 docsify 文档网站。我们可以使用本地或者远程文件。

配置好了以后，我们可以在本地预览。

```bash
npm start

# open http://localhost:4000
```

发布！

```bash
now -p
```

现在，你有一个支持服务端渲染的文档网站了。

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

模板可以包含占位符，会自动将渲染后的 html 和配置内容注入到页面上。

 - `<!--inject-app-->`
 - `<!--inject-config-->`


## 配置

配置可以单独写在配置文件内，然后通过 `--config config.js` 加载，或者写在 `package.json` 中。

渲染的基础模版也可以自定义，配置在 `template` 属性上。

```js
module.exports = {
  template: './ssr.html',
  maxAge: 60 * 60 * 1000, // lru-cache 设置
  config: {
   // docsify 设置
  }
}
```




## 更多玩法

你可以直接在你的 Node 服务器上执行 `docsify start` 。

`docsify start` 其实是依赖了 [`docsify-server-renderer`](https://npmarket.surge.sh/?name=docsify-server-renderer) 模块，如果你感兴趣，你完全可以用它自己实现一个 server，可以加入缓存等功能。

```js
var Renderer = require('docsify-server-renderer')
var readFileSync = require('fs').readFileSync

// init
var renderer = new Renderer({
  template: readFileSync('./docs/index.template.html', 'utf-8'),
  config: {
    name: 'docsify',
    repo: 'docsifyjs/docsify'
  }
})

renderer.renderToString(url)
  .then(html => {})
  .catch(err => {})
```

当然文档文件和 server 也是可以部署在一起的，`basePath` 不是一个 URL 的话就会当做文件路径处理，也就是从服务器上加载资源。
