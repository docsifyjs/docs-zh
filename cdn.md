# CDN

推荐使用 [jsDelivr](//cdn.jsdelivr.net)，能及时获取到最新版。你也可以在[cdn.jsdelivr.net/npm/docsify/](cdn.jsdelivr.net/npm/docsify/)中浏览npm包的源代码。

## 获取最新版本

不指定特定版本号时将引入最新版。

```html
<!-- 引入 css -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css">

<!-- 引入 script -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.js"></script>
```

也可以使用 [压缩版文件](#compressed-file).

## 获取指定版本

如果担心频繁地版本更新又可能引入未知 Bug，我们也可以使用具体的版本。规则是 `//cdn.jsdelivr.net/npm/docsify@VERSION/`

```html
<!-- 引入 css -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4.10.2/themes/vue.css">

<!-- 引入 script -->
<script src="//cdn.jsdelivr.net/npm/docsify@4.10.2/lib/docsify.js"></script>
```

!> 指定 *VERSION* 为 `latest` 可以强制每次都请求最新版本。

## 压缩版

CSS 的压缩文件位于 `/lib/themes/` 目录下，JS 的压缩文件是原有文件路径的基础上加 `.min` 后缀。

```html
<!-- 引入 css -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css">

<!-- 引入 script -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

```html
<!-- 引入 css -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4.10.2/lib/themes/vue.css">

<!-- 引入 script -->
<script src="//cdn.jsdelivr.net/npm/docsify@4.10.2/lib/docsify.min.js"></script>
```

## 其他 CDN

- https://www.bootcdn.cn/docsify/ (支持国内)
- https://cdn.jsdelivr.net/npm/docsify/ (国内外都支持)
- https://cdnjs.com/libraries/docsify
- https://unpkg.com/browse/docsify/

