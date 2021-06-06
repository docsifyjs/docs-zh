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

      // 搜索标题的最大层级, 1 - 6
      depth: 2,

      hideOtherSidebarContent: false, // 是否隐藏其他侧边栏内容

      // 避免搜索索引冲突
      // 同一域下的多个网站之间
      namespace: 'website-1',

      // 使用不同的索引作为路径前缀（namespaces）
      // 注意：仅适用于 paths: 'auto' 模式
      //
      // 初始化索引时，我们从侧边栏查找第一个路径
      // 如果它与列表中的前缀匹配，我们将切换到相应的索引
      pathNamespaces: ['/zh-cn', '/ru-ru', '/ru-ru/v1'],

      // 您可以提供一个正则表达式来匹配前缀。在这种情况下，
      // 匹配到的字符串将被用来识别索引
      pathNamespaces: /^(\/(zh-cn|ru-ru))?(\/(v1|v2))?/
    }
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

当执行全文搜索时，该插件会忽略双音符（例如，"cafe" 也会匹配 "café"）。像 IE11 这样的旧版浏览器需要使用以下 [String.normalize()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize) polyfill 来忽略双音符：

```html
<script src="//polyfill.io/v3/polyfill.min.js?features=String.prototype.normalize"></script>
```

## 谷歌统计 - Google Analytics

需要配置 track id 才能使用。

```html
<script>
  window.$docsify = {
    ga: 'UA-XXXXX-Y'
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/ga.min.js"></script>
```

也可以通过 `data-ga` 配置 id。

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js" data-ga="UA-XXXXX-Y"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/ga.min.js"></script>
```

## emoji

默认是提供 emoji 解析的，能将类似 `:100:` 解析成 :100:。但是它不是精准的，因为没有处理非 emoji 的字符串。如果你需要正确解析 emoji 字符串，你可以引入这个插件。

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```

?> 如果你不想解析成表情符号，可以使用__colon_<span>_</span>或`&#58;`。如果你需要在标题中使用，我们建议使用`&#58;`。例如，`&#58;100:`。

## 外链脚本 - External Script

如果文档里的 script 是内联脚本，可以直接执行；而如果是外链脚本（即 js 文件内容由 `src` 属性引入），则需要使用此插件。

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/external-script.min.js"></script>
```

## 图片缩放 - Zoom image

Medium's 风格的图片缩放插件. 基于 [medium-zoom](https://github.com/francoischalifour/medium-zoom)。

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
```

忽略某张图片

```markdown
![](image.png ":no-zoom")
```

## 在 Github 上编辑

在每一页上添加 `Edit on github` 按钮. 由第三方库提供, 查看 [document](https://github.com/njleonzhang/docsify-edit-on-github)

## 代码即时预览和 jsfiddle 集成

通过这个插件，示例代码可以在页面上即时呈现，让读者可以立即看到预览。当读者展开演示框时，源码和说明就会显示在那里，如果点击`Try in Jsfiddle`按钮，`jsfiddle.net`就会打开这个例子的代码，让读者自己修改代码和测试。

docsify同时支持[Vue](https://njleonzhang.github.io/docsify-demo-box-vue/)和[React](https://njleonzhang.github.io/docsify-demo-box-react/)版本的插件。

## 复制到剪贴板

在所有的代码块上添加一个简单的`Click to copy`按钮来允许用户从你的文档中轻易地复制代码。由[@jperasmus](https://github.com/jperasmus)提供。

```html
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
```

详情可参考 [README.md](https://github.com/jperasmus/docsify-copy-code/blob/master/README.md) 。

## Disqus

Disqus评论系统支持。 https://disqus.com/

```html
<script>
  window.$docsify = {
    disqus: 'shortname'
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/disqus.min.js"></script>
```

## Gitalk

[Gitalk](https://github.com/gitalk/gitalk)，一个现代化的，基于Preact和Github Issue的评论系统。

```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.css">

<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/gitalk.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.js"></script>
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
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

从[这里](https://github.com/imyelo/docsify-pagination#readme)获取更多信息。

## 字数统计

这是一款为docsify提供文字统计的插件. [@827652549](https://github.com/827652549)提供

它提供了统计中文汉字和英文单词的功能，并且排除了一些markdown语法的特殊字符例如*、-等

**Add JS**
```html
<script src="//unpkg.com/docsify-count/dist/countable.js"></script>
```

**Add settings**
```js
window.$docsify = {
  count:{
    countable:true,
    fontsize:'0.9em',
    color:'rgb(90,90,90)',
    language:'chinese'
  }
}
```

check [document](https://github.com/827652549/docsify-count)


## Code Fund

帮你快速接入[Code Fund](https://codesponsor.io/)的[插件](https://github.com/njleonzhang/docsify-plugin-codefund), 由[@njleonzhang](https://github.com/njleonzhang)提供。

> Code Fund 以前叫 codesponsor

```
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>

window.$docsify = {
  plugins: [
    DocsifyCodefund.create('51d43327-eea3-4e27-bd44-e075e67a84fb') // 把这个id改成你的codefund id
  ]
}
```

## Tabs

这个插件用来在 Markdown 中显示选项卡。

- [文档和示例](https://jhildenbiddle.github.io/docsify-tabs)

开发：[@jhildenbiddle](https://github.com/jhildenbiddle/docsify-tabs).

## 更多插件

参考 [awesome-docsify](awesome?id=plugins)
