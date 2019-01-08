# 插件列表

## 全文搜索 - Search

全文搜索插件会根据当前页面上的超链接获取文档内容，在 `localStorage` 内建立文档索引。默认过期时间为一天，当然我们可以自己指定需要缓存的文件列表或者配置过期时间。

```html
<script>
  window.$docsify = {
    search: 'auto', // 默认值

    search : [
      '/',            // => /README.md
      '/guide',       // => /guide.md
      '/get-started', // => /get-started.md
      '/zh-cn/',      // => /zh-cn/README.md
    ],

    // 完整配置参数
    search: {
      maxAge: 86400000, // 过期时间，单位毫秒，默认一天
      paths: [], // or 'auto'
      placeholder: 'Type to search',

      // 支持本地化
      placeholder: {
        '/zh-cn/': '搜索',
        '/': 'Type to search'
      },

      noData: 'No Results!',

      // 支持本地化
      noData: {
        '/zh-cn/': '找不到结果',
        '/': 'No Results'
      },

      // 搜索标题的最大程级, 1 - 6
      depth: 2
    }
  }
</script>
<script src="//unpkg.com/docsify"></script>
<script src="//unpkg.com/docsify/lib/plugins/search.js"></script>
```

## 谷歌统计 - Google Analytics

需要配置 track id 才能使用。

```html
<script>
  window.$docsify = {
    ga: 'UA-XXXXX-Y'
  }
</script>
<script src="//unpkg.com/docsify"></script>
<script src="//unpkg.com/docsify/lib/plugins/ga.js"></script>
```

也可以通过 `data-ga` 配置 id。

```html
<script src="//unpkg.com/docsify" data-ga="UA-XXXXX-Y"></script>
<script src="//unpkg.com/docsify/lib/plugins/ga.js"></script>
```

## emoji

默认是提供 emoji 解析的，能将类似 `:100:` 解析成 :100:。但是它不是精准的，因为没有处理非 emoji 的字符串。如果你需要正确解析 emoji 字符串，你可以引入这个插件。

```html
<script src="//unpkg.com/docsify/lib/plugins/emoji.js"></script>
```

## 外链脚本 - External Script

如果文档里的 script 是内联脚本，可以直接执行；而如果是外链脚本（即 js 文件内容由 `src` 属性引入），则需要使用此插件。

```html
<script src="//unpkg.com/docsify/lib/plugins/external-script.js"></script>
```

## Demo code with instant preview and jsfiddle integration

使用这个插件，示例代码可以在页面上立刻渲染，这样就可以立刻看到效果。当示例框被展开时，源码和描述会被显示出来，如果他们点击`Try in Jsfiddle`这个按钮，将会在`jsfiddle.net`中打开一个包含这些示例代码的项目，这样就可以修改源码和测试了。

docsify同时支持[Vue](https://njleonzhang.github.io/docsify-demo-box-vue/)和[React](https://njleonzhang.github.io/docsify-demo-box-react/)版本的插件。

## 图片缩放 - Zoom image

Medium's 风格的图片缩放插件. 基于 [medium-zoom](https://github.com/francoischalifour/medium-zoom)。

```html
<script src="//unpkg.com/docsify/lib/plugins/zoom-image.js"></script>
```

忽略某张图片

```markdown
![](image.png ':no-zoom')
```

## 在 Github 上编辑

在每一页上添加 `Edit on github` 按钮. 由第三方库提供, 查看 [document](https://github.com/njleonzhang/docsify-edit-on-github)

## 复制到剪贴板

在所有的代码块上添加一个简单的`Click to copy`按钮来允许用户从你的文档中轻易地复制代码。由[@jperasmus](https://github.com/jperasmus)提供。

```html
<script src="//unpkg.com/docsify-copy-code"></script>
```

从[这里](https://github.com/jperasmus/docsify-copy-code#readme)获取更多信息。

## Disqus

Disqus评论系统支持。 https://disqus.com/

```html
<script>
  window.$docsify = {
    disqus: 'shortname'
  }
</script>
<script src="//unpkg.com/docsify/lib/plugins/disqus.min.js"></script>
```

## Gitalk

[Gitalk](https://github.com/gitalk/gitalk)，一个现代化的，基于Preact和Github Issue的评论系统。

```html
<link rel="stylesheet" href="//unpkg.com/gitalk/dist/gitalk.css">

<script src="//unpkg.com/docsify/lib/plugins/gitalk.min.js"></script>
<script src="//unpkg.com/gitalk/dist/gitalk.min.js"></script>
<script>
  const gitalk = new Gitalk({
    clientID: 'Github Application Client ID',
    clientSecret: 'Github Application Client Secret',
    repo: 'Github repo',
    owner: 'Github repo owner',
    admin: ['Github repo collaborators, only these guys can initialize github issues'],
    // facebook-like distraction free mode
    distractionFreeMode: false
  })
</script>
```

## Pagination

docsify的分页导航插件，由[@imyelo](https://github.com/imyelo)提供。

```html
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

从[这里](https://github.com/imyelo/docsify-pagination#readme)获取更多信息。

## Code Fund

帮你快速接入[Code Fund](https://codesponsor.io/)的[插件](https://github.com/njleonzhang/docsify-plugin-codefund), 由[@njleonzhang](https://github.com/njleonzhang)提供。

> Code Fund 以前叫 codesponsor

```
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>

window.$docsify = {
  plugins: [
    DocsifyCodefund.create('51d43327-eea3-4e27-bd44-e075e67a84fb') // 把这个id改成你的codefund id
  ]
}
```
