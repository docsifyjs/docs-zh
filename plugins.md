# 插件列表

## 全文搜索

默认情况下，当前页面上的超链接会被识别，内容会被保存到 `IndexedDB`。 你也可以指定文件的路径。

<!-- prettier-ignore -->

```html
<script>
  window.$docsify = {
    search: 'auto', // default

    search: [
      '/',            // => /README.md
      '/guide',       // => /guide.md
      '/get-started', // => /get-started.md
      '/zh-cn/',      // => /zh-cn/README.md
    ],

    // Complete configuration parameters
    search: {
      // Location in sidebar (default: prepended as first child)
      // Optionally specify insertAfter or insertBefore (not both)
      insertAfter: '.app-name', // CSS selector in .sidebar scope
      insertBefore: '.sidebar-nav', // CSS selector in .sidebar scope

      maxAge: 86400000, // Expiration time, the default one day
      paths: [], // or 'auto'
      placeholder: 'Type to search',

      // Localization
      placeholder: {
        '/zh-cn/': '搜索',
        '/': 'Type to search',
      },

      noData: 'No Results!',

      // Localization
      noData: {
        '/zh-cn/': '找不到结果',
        '/': 'No Results',
      },

      // Headline depth, 1 - 6
      depth: 2,

      hideOtherSidebarContent: true, // Deprecated as of v5

      // To avoid search index collision
      // between multiple websites under the same domain
      namespace: 'website-1',

      // Use different indexes for path prefixes (namespaces).
      // NOTE: Only works in 'auto' mode.
      //
      // When initialiazing an index, we look for the first path from the sidebar.
      // If it matches the prefix from the list, we switch to the corresponding index.
      pathNamespaces: ['/zh-cn', '/ru-ru', '/ru-ru/v1'],

      // You can provide a regexp to match prefixes. In this case,
      // the matching substring will be used to identify the index
      pathNamespaces: /^(\/(zh-cn|ru-ru))?(\/(v1|v2))?/,
    },
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/search.min.js"></script>
```

在进行全文搜索时，该插件会忽略变音标记（例如："cafe" 也会匹配 "café"）。

## 谷歌统计 - Google Analytics

> 从 2023 年 7 月 1 日起，谷歌的通用分析服务将不再处理标准属性中的新数据。 通过设置并切换到 Google Analytics 4 属性和 docsify 的 gtag.js 插件做好准备。

安装插件并配置 track id。

```html
<script>
  window.$docsify = {
    ga: 'UA-XXXXX-Y',
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/ga.min.js"></script>
```

也可以通过 `data-ga` 配置 id。

<!-- prettier-ignore -->

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js" data-ga="UA-XXXXX-Y"></script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/ga.min.js"></script>
```

## Google Analytics 4 (GA4)

安装插件并配置 track id。

```html
<script>
  // Single ID
  window.$docsify = {
    gtag: 'UA-XXXXX-Y',
  };

  // Multiple IDs
  window.$docsify = {
    gtag: [
      'G-XXXXXXXX', // Google Analytics 4 (GA4)
      'UA-XXXXXXXX', // Google Universal Analytics (GA3)
      'AW-XXXXXXXX', // Google Ads
      'DC-XXXXXXXX', // Floodlight
    ],
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/gtag.min.js"></script>
```

## emoji

显示更多的表情符号短代码。 如果没有这个插件，Docsify 只能渲染数量有限的表情短代码。

!> 自 v4.13 起已弃用。 Docsify 不再需要此插件来提供完整的 emoji 支持。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/emoji.min.js"></script>
```

## 外链脚本 - External Script

如果文档里的 script 是内联脚本，可以直接执行；而如果是外链脚本（即 js 文件内容由 `src` 属性引入），则需要使用此插件。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/external-script.min.js"></script>
```

## 图片缩放 - Zoom image

Medium's 风格的图片缩放插件。 基于 [medium-zoom](https://github.com/francoischalifour/medium-zoom)。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/zoom-image.min.js"></script>
```

排除某张图片

```markdown
![](image.png ':no-zoom')
```

## 在 GitHub 上编辑

在每一页上添加 `Edit on github` 按钮。 由[@njleonzhang](https://github.com/njleonzhang) 提供，查看[文档](https://github.com/njleonzhang/docsify-edit-on-github)

## 代码即时预览和 jsfiddle 集成

有了这个插件，示例代码就能立即呈现在页面上，这样读者就能立即看到预览效果。
当读者展开演示框时，源代码和说明就会显示出来。 如果点击 `Try in Jsfiddle` 按钮，`jsfiddle.net` 就会打开这个例子的代码，让读者自己修改代码和测试。

[Vue](https://njleonzhang.github.io/docsify-demo-box-vue/) 和 [React](https://njleonzhang.github.io/docsify-demo-box-react/) 都支持。

## 复制到剪贴板

在所有的代码块上添加一个简单的 `Click to copy` 按钮来允许用户从你的文档中轻易地复制代码。 由 [@jperasmus](https://github.com/jperasmus) 提供

```html
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
```

详情可参考 [README](https://github.com/jperasmus/docsify-copy-code/blob/master/README.md)。

## Disqus

Disqus 评论。 https://disqus.com/

```html
<script>
  window.$docsify = {
    disqus: 'shortname',
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/disqus.min.js"></script>
```

## Gitalk

[Gitalk](https://github.com/gitalk/gitalk) 是一个基于 GitHub Issue 和 Preact 的现代评论组件。

```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.css" />

<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/gitalk.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.js"></script>
<script>
  const gitalk = new Gitalk({
    clientID: 'GitHub Application Client ID',
    clientSecret: 'GitHub Application Client Secret',
    repo: 'GitHub repo',
    owner: 'GitHub repo owner',
    admin: [
      'GitHub repo collaborators, only these guys can initialize github issues',
    ],
    // facebook-like distraction free mode
    distractionFreeMode: false,
  });
</script>
```

## Pagination

docsify 的分页导航插件。 由 [@imyelo](https://github.com/imyelo) 提供

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

从[这里](https://github.com/imyelo/docsify-pagination#readme)获取更多信息。

## Tabs

用来在 markdown 中显示选项卡的插件。

- [文档和示例](https://jhildenbiddle.github.io/docsify-tabs)

由 [@jhildenbiddle](https://github.com/jhildenbiddle/docsify-tabs) 提供。

## 更多插件

参考 [awesome-docsify](zh-cn/awesome?id=plugins)
