# CDN

Docsify 的 [npm package](https://www.npmjs.com/package/docsify) 是随着每个版本自动发布到 CDN 中的。 内容可以在每个 CDN 上查看。

Docsify 推荐 [jsDelivr](//cdn.jsdelivr.net) 为其首选的 CDN：

- https://cdn.jsdelivr.net/npm/docsify/ (国内外都支持)

在没有 jsDelivr 的地方，也可能需要其他的 CDN：

- https://cdnjs.com/libraries/docsify
- https://unpkg.com/browse/docsify/
- https://www.bootcdn.cn/docsify/ (支持国内)

## 指定版本

请注意以下 CDN URL 中的`@`版本锁定。 这样就可以指定最新的主版本、次版本、补丁或特定 [semver](https://semver.org) 版本号。

- MAJOR 版本包括不兼容变更<br>
  `1.0.0` → `2.0.0`
- MINOR 版本包括兼容性的新功能<br>
  `1.0.0` → `1.1.0`
- PATCH版本包括兼容性的错误修复<br>
  `1.0.0` → `1.0.1`

从文件名中移除`.min`，可获取未压缩的资源。

## 最新主要版本

指定最新的主要版本允许您的网站在发布时接收所有非破坏性的增强("次级"更新)和错误修复("补丁"更新)。 对于那些倾向于零维护又可以随着新版本的发布更新其网站的风险最小化的人来说，这是一个好的选择。

?> 发布新的主要版本时，你需要在你的 CDN URLs 中的 `@` 符号后手动更新主要版本号。

<!-- prettier-ignore -->

```html
<!-- 主题 -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/themes/vue.min.css" />

<!-- Docsify -->
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
```

## 获取指定版本 :id=specific-version

指定一个准确的版本可以防止将来的任何更新影响你的网站。 对于那些愿意在发布新版本时手动更新资源的人来说，这是一个很好的选项。

?> 新版本发布后，你需要在你的 CDN URLs 中的 '@' 符号后手动更新版本号。

<!-- prettier-ignore -->

```html
<!-- 主题 -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5.0.0/themes/vue.min.css" />

<!-- Docsify -->
<script src="//cdn.jsdelivr.net/npm/docsify@5.0.0/dist/docsify.min.js"></script>
```
