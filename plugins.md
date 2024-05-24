# 插件列表

## 全文搜索 - Search

默认情况下，当前页面上的超链接会被识别，内容会被保存到“localStorage”。 您也可以指定文件的路径。

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

    // complete configuration parameters
    search: {
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

      hideOtherSidebarContent: false, // whether or not to hide other sidebar content

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

全文搜索插件会根据当前页面上的超链接获取文档内容，在 `localStorage` 内建立文档索引。默认过期时间为一天，当然我们可以自己指定需要缓存的文件列表或者配置过期时间。

## 谷歌统计 - Google Analytics

> 谷歌的通用分析服务将不再处理标准属性中的新数据，2023年7月1日开始。 通过设置并切换到 Google Analytics 4 属性和 docsify 的 gtag.js 插件做好准备。

安装插件并配置音轨ID。

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

安装插件并配置音轨ID。

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

呈现更大的表情缩短代码集。 没有这个插件，Docsify只能渲染数量有限的表情短码。

!> 废弃为 v4.13。 Docsify 不再需要此插件来提供完整的 emoji 支持。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/emoji.min.js"></script>
```

## 外链脚本 - External Script

如果文档里的 script 是内联脚本，可以直接执行；而如果是外链脚本（即 js 文件内容由 `src` 属性引入），则需要使用此插件。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/external-script.min.js"></script>
```

## 图片缩放 - Zoom image

Medium's 风格的图片缩放插件. 基于 [medium-zoom](https://github.com/francoischalifour/medium-zoom)。

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/zoom-image.min.js"></script>
```

排除特殊图像

```markdown
![](image.png ":no-zoom")
```

## 在 Github 上编辑

在每一页上添加 `Edit on github` 按钮. 由第三方库提供, 查看 [document](https://github.com/njleonzhang/docsify-edit-on-github)

## 代码即时预览和 jsfiddle 集成

docsify的分页导航插件，由[@imyelo](https://github.com/imyelo)提供。
当读者扩展演示框时，源代码和描述会在这里显示。 通过这个插件，示例代码可以在页面上即时呈现，让读者可以立即看到预览。当读者展开演示框时，源码和说明就会显示在那里，如果点击`Try in Jsfiddle`按钮，`jsfiddle.net`就会打开这个例子的代码，让读者自己修改代码和测试。

docsify同时支持[Vue](https://njleonzhang.github.io/docsify-demo-box-vue/)和[React](https://njleonzhang.github.io/docsify-demo-box-react/)版本的插件。

## 复制到剪贴板

在所有的代码块上添加一个简单的`Click to copy`按钮来允许用户从你的文档中轻易地复制代码。由[@jperasmus](https://github.com/jperasmus)提供。 由 [@jperasmus ](https://github.com/jperasmus) 提供

```html
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
```

详情可参考 [README.md](https://github.com/jperasmus/docsify-copy-code/blob/master/README.md) 。

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

[Gitalk](https://github.com/gitalk/gitalk)，一个现代化的，基于Preact和Github Issue的评论系统。

```html
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.css" />

<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/gitalk.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.js"></script>
<script>
  const gitalk = new Gitalk(请注意，
    clientID: 'Github 应用程序客户端 ID',
    客户端密钥：“Github 应用程序客户端保密”，
    仓库：“Github 仓库”
    所有者: 'Github repo owners'
    管理员: [
      'Github repo collaborators, 只有这些用户可以初始化 github 问题'，
    ],
    // facebook-like distraction free mode
    distractionFreeMode: false,
  };
</script>
```

## 分页

分页供文档化。 [@827652549](https://github.com/827652549)提供

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

从[这里](https://github.com/imyelo/docsify-pagination#readme)获取更多信息。

## Tabs

用于显示Markdown标签内容的 docsify.js 插件。

- [文档和示例](https://jhildenbiddle.github.io/docsify-tabs)

开发：[@jhildenbiddle](https://github.com/jhildenbiddle/docsify-tabs).

## 更多插件

参考 [awesome-docsify](awesome?id=plugins)
