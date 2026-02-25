# 将 v4 升级到 v5

将 Docsify v4 网站升级到 v5 时的主要更改涉及更新 CDN URL 和主题文件。 你的配置设置基本保持不变，因此升级相当简单。

## 开始之前

一些旧版 Docsify 网站可能使用非版本锁定 URL，如：

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

如果你的网站使用不含 `@4` 或特定版本号的 URL，请按照以下相同步骤操作。 你需要更新版本说明符和路径结构。

## 分步说明

### 1. 更新主题 CSS

**更换主题（v4）：**

```html
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css"
/>
<!-- OR if you have non-versioned URL: -->
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css"
/>
```

**使用这个 (v5)：**

```html
<!-- Core Theme -->
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/core.min.css"
/>
<!-- Optional: Dark Mode Support -->
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/addons/core-dark.min.css"
  media="(prefers-color-scheme: dark)"
/>
```

**注：** 如果你使用的是不同的 v4 主题（buble、dark、pure），v5 核心主题将取代这些主题，不过如果你喜欢，Vue 和 Dark 主题可作为附加组件提供。

查看[主题](zh-cn/themes.md) 了解更多详情。

### 2. 添加可选的 Body Class（用于设计风格）

**更新开头的 body tag：**

```html
<body class="sidebar-chevron-right"></body>
```

这将在侧边栏中添加一个 chevron 指示器。 如果你愿意，也可以省略。

查看[主题类](zh-cn/themes.md?id=classes) 了解更多详情。

### 3. 更新 Docsify 主脚本

**修改：**

```html
<script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/docsify.min.js"></script>
<!-- OR if you have non-versioned URL: -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

**为：**

```html
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
```

### 4. 更新插件 URL

**搜索插件：**\*

```html
<!-- v4 -->
<script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.js"></script>
<!-- OR non-versioned: -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.js"></script>

<!-- v5 -->
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/search.min.js"></script>
```

**缩放插件：**

```html
<!-- v4 -->
<script src="https://cdn.jsdelivr.net/npm/docsify@4/lib/plugins/zoom-image.min.js"></script>
<!-- OR non-versioned: -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>

<!-- v5 -->
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/zoom.min.js"></script>
```

**注意：** 如果你使用其他 Docsify 插件（如 emoji、external-script、front-matter 等），则需要按照相同的模式更新这些 URL：

- 将 `/lib/plugins/` 改为 `/dist/plugins/`
- 将版本号从 `@4`（或无版本）更新为 `@5`
- 例如：`//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js`变为`//cdn.jsdelivr.net/npm/docsify@5/dist/plugins/emoji.min.js`

## 主要区别摘要

- **CDN 路径**：从 `/lib/` 改为 `/dist/`
- **版本**：从 `@4` 更新到 `@5`
- **主题**：v5 使用核心主题（可选附加组件）
- **插件名称**：`zoom-image` → `zoom`

## 附加说明

- 你在 `window.$docsify` 中的配置保持不变
- 所有 markdown 内容保持不变
- 对于大多数网站来说，此次升级不会造成中断（但不再支持 Internet Explorer 11 等传统浏览器）
- 为保持与 Docsify v4 相同的视觉风格，可使用 [Vue 主题（附加组件）](zh-cn/themes.md?id=vue-theme-add-on)
- 针对 v4 特定主题类或元素的自定义 CSS 可能需要针对 v5 进行更新
- v5 核心主题可使用 CSS 变量进行自定义 - 详情请查看[主题自定义](zh-cn/themes.md?id=customization)

就是这样！ 你的 Docsify 网站现在应该运行在 v5 版本上。
