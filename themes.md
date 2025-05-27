# 主题

## 核心主题 :id=core-theme

Docsify "核心" 主题包含呈现 Docsify 网站所需的所有样式和[主题属性](#theme-properties)。 该主题可单独用作简约主题，与[主题附加组件](#theme-add-ons)结合使用，使用核心[类](#classes)进行修改，也可作为[自定义](#customization)的起点。

<!-- prettier-ignore -->

```html
<!-- Core Theme -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/core.min.css" />
```

## 主题附加组件

主题附加组件与[核心主题](#core-theme)结合使用。 附加组件包含修改[主题属性](#theme-properties)值和/或添加自定义样式声明的 CSS 规则。 它们通常（但不总是）可以与其他附加组件一起使用。

!> 主题附加组件必须在[核心主题](#core-theme)之后加载。

<!-- prettier-ignore -->

```html
<!-- Core Theme -->
<link rel="stylesheet" href="..." />

<!-- Theme (add-on) -->
<link rel="stylesheet" href="..." />
```

### 核心深色（附加组件）

[核心主题](#core-theme)的深色模式样式。 只有在操作系统的暗模式激活时，才能通过指定 `media` 属性来应用样式。

<label>
  <input
    class="toggle"
    type="checkbox"
    value="core-dark"
    data-group="addon"
    data-sheet
  >
  Preview Core Dark
</label>
<br>
<label>
  <input
    class="toggle"
    type="checkbox"
    value="core-dark-auto"
    data-group="addon"
    data-sheet
  >
  Preview Core Dark (Dark Mode Only)
</label>

<!-- prettier-ignore -->

```html
<!-- Core Dark (add-on) -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/addons/core-dark.min.css" />
```

<!-- prettier-ignore -->

```html
<!-- Core Dark - Dark Mode Only (add-on) -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/addons/core-dark.min.css" media="(prefers-color-scheme: dark)" />
```

### Vue 主题（附加组件）

备受欢迎的 Docsify v4 主题。

<label>
  <input
   class="toggle"
   type="checkbox"
   value="vue"
   data-group="addon"
   data-sheet
  >
  Preview Vue
</label>

<!-- prettier-ignore -->

```html
<!-- Vue Theme (add-on) -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/addons/vue.min.css" />
```

## 类

[核心主题](#core-theme)提供了多个 CSS 类，用于自定义 Docsify 网站。 这些类应用于 `index.html` 页面中的 `<body>` 元素。

<!-- prettier-ignore -->

```html
<body class="...">
```

### 加载中

在等待 Docsify 初始化时显示加载动画。

<!-- prettier-ignore -->

```html
<body class="loading">
```

<output data-lang="output">
  <div class="loading" style="margin: auto;"></div>
</output>

### 侧边栏格线

在侧边栏的页面链接上显示展开/折叠图标。

<label>
  <input class="toggle" type="checkbox" value="sidebar-chevron-right" data-class data-group="sidebar-chevron"> Preview <code>sidebar-chevron-right</code>
</label>
<br>
<label>
  <input class="toggle" type="checkbox" value="sidebar-chevron-left" data-class data-group="sidebar-chevron"> Preview <code>sidebar-chevron-left</code>
</label>

<!-- prettier-ignore -->

```html
<body class="sidebar-chevron-right">
```

<!-- prettier-ignore -->

```html
<body class="sidebar-chevron-left">
```

要防止在特定页面链接上显示 chevrons，请添加 `no-chevron` 类，如下所示：

```md
[My Page](page.md ':class=no-chevron')
```

**主题属性**

<!-- prettier-ignore -->

```css
:root {
  --sidebar-chevron-collapsed-color: var(--color-mono-3);
  --sidebar-chevron-expanded-color : var(--theme-color);
}
```

### 侧边栏组

在侧边栏的链接组之间添加视觉区分。

<label>
  <input class="toggle" type="checkbox" value="sidebar-group-box" data-class data-group="sidebar-group"> Preview <code>sidebar-group-box</code>
</label>
<br>
<label>
  <input class="toggle" type="checkbox" value="sidebar-group-underline" data-class data-group="sidebar-group"> Preview <code>sidebar-group-underline</code>
</label>

<!-- prettier-ignore -->

```html
<body class="sidebar-group-box">
```

<!-- prettier-ignore -->

```html
<body class="sidebar-group-underline">
```

### 侧边栏链接夹

将多行侧边栏链接限制为单行，后加省略号。

<label>
  <input class="toggle" type="checkbox" value="sidebar-link-clamp" data-class>
  Preview <code>sidebar-link-clamp</code>
</label>

<!-- prettier-ignore -->

```html
<body class="sidebar-link-clamp">
```

### 侧边栏切换

在侧边栏切换按钮中显示 "hamburger" 图标（三行），而不是默认的 "kebab" 图标。

<label>
  <input class="toggle" type="checkbox" value="sidebar-toggle-chevron" data-class data-group="sidebar-toggle">
  Preview <code>sidebar-toggle-chevron</code>
</label>
<br>
<label>
  <input class="toggle" type="checkbox" value="sidebar-toggle-hamburger" data-class data-group="sidebar-toggle">
  Preview <code>sidebar-toggle-hamburger</code>
</label>

<!-- prettier-ignore -->

```html
<body class="sidebar-toggle-chevron">
```

<!-- prettier-ignore -->

```html
<body class="sidebar-toggle-hamburger">
```

## 定制

Docsify 提供了[主题属性](#theme-properties)以简化对经常修改的样式的自定义。

1. 在 `index.html` 中的主题样式表后添加一个 `<style>` 标签。

  <!-- prettier-ignore -->

  ```html
  <!-- Theme -->
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@5/dist/themes/core.min.css" />

  <!-- Custom theme styles -->
  <style>
    :root {
      /* ... */
    }
  </style>
  ```

  主题属性也可以在 markdown 中按页面设置。

  ```markdown
  # My Heading

  Hello, World!

  <style>
    :root {
      /* ... */
    }
  </style>
  ```

2. 在 `:root` 声明中设置自定义[主题属性](#theme-properties)。

  <!-- prettier-ignore -->

  ```css
  :root {
    --theme-color: red;
    --font-size  : 15px;
    --line-height: 1.5;
  }
  ```

  自定义[主题属性](#theme-properties)可有条件地应用于浅色和/或深色模式。

  <!-- prettier-ignore -->

  ```css
  /* Light and dark mode */
  :root {
    --theme-color: pink;
  }

  /* Light mode only */
  @media (prefers-color-scheme: light) {
    :root {
      --color-bg  : #eee;
      --color-text: #444;
    }
  }

  /* Dark mode only */
  @media screen and (prefers-color-scheme: dark) {
    :root {
      --color-bg  : #222;
      --color-text: #ddd;
    }
  }
  ```

3. 可通过添加网络字体资源并根据需要修改 `--font-family` 属性来使用自定义字体：

  <!-- prettier-ignore -->

  ```css
  /* Fonts: Noto Sans, Noto Emoji, Noto Mono */
  @import url('https://fonts.googleapis.com/css2?family=Noto+Color+Emoji&family=Noto+Sans+Mono:wght@100..900&family=Noto+Sans:ital,wght@0,100..900;1,100..900&display=swap');

  :root {
    --font-family      : 'Noto Sans', sans-serif;
    --font-family-emoji: 'Noto Color Emoji', sans-serif;
    --font-family-mono : 'Noto Sans Mono', monospace;
  }
  ```

?> **主题作者**：考虑提供手动加载推荐网络字体的说明，而不是在主题中使用 `@import`。 这样喜欢不同字体的用户就可以避免不必要地加载你所推荐的网页字体。

4. 高级样式可能需要自定义 CSS 声明。 这在意料之中，但当 Docsify 发布新版本时，自定义 CSS 声明可能会中断。 在可能的情况下，请使用[主题属性](#theme-properties) 而不是自定义声明，或者将[CDN](zh-cn/cdn) URL 锁定为[特定版本](zh-cn/cdn#specific-version)，以避免在使用自定义 CSS 声明时出现潜在问题。

  ```css
  .sidebar li.active > a {
    border-right: 3px solid var(--theme-color);
  }
  ```

## 主题属性 :id=theme-properties

以下属性在所有官方 Docsify 主题中都可用。 显示的是"核心"主题的默认值。

?> **主题和插件作者**：我们鼓励你利用这些自定义主题属性，并在你的项目中提供类似的自定义选项。

### Common

以下是最常修改的主题属性。 [Advanced](#advanced) 主题属性也可以使用，但通常不需要修改。

<!-- TODO: Replace TBD with include CSS include below -->

**TBD**

<!-- [vars.css](https://raw.githubusercontent.com/docsifyjs/docsify/main/src/themes/shared/_vars.css ':include') -->

### Advanced

Advanced 主题属性也可供使用，但通常无需修改。 从 [common](#common) 主题属性导出的值，但也可根据需要明确设置。

<!-- TODO: Replace TBD with include CSS include below -->

**TBD**

<!-- [vars.css](https://raw.githubusercontent.com/docsifyjs/docsify/main/src/themes/shared/_vars.css ':include') -->

## 社区

有关其他社区主题，请参见 [Awesome Docsify](zh-cn/awesome)。

<script>
  (function () {
    const toggleElms = Docsify.dom.findAll(
      'input:where([data-class], [data-sheet])',
    );
    const previewSheets = Docsify.dom.findAll(
      'link[rel="stylesheet"][data-sheet]',
    );

    function handleChange(e) {
      const elm = e.target.closest('[data-class], [data-sheet]');
      const value = elm.value;
      const groupVal = elm.getAttribute('data-group');
      const radioGroupName = elm.matches('[type="radio"]') ? elm.name : undefined;

      // Toggle class
      if (elm.matches('[data-class]')) {
        document.body.classList.toggle(value, elm.checked);
      }
      // Toggle sheet
      else {
        const themeSheet = previewSheets.find(
          sheet => sheet.getAttribute('data-sheet') === value,
        );

        themeSheet && (themeSheet.disabled = !elm.checked);
      }

      if (!elm.checked || (!groupVal && !radioGroupName)) {
        return;
      }

      // Group elements & values
      const groupElms = toggleElms.filter(elm =>
        groupVal
          ? groupVal === elm.getAttribute('data-group')
          : radioGroupName === elm.name,
      );
      const groupVals = groupElms.map(elm => elm.value);

      if (groupElms.length <= 1) {
        return;
      }

      if (groupVal) {
        // Uncheck other group elements
        groupElms.forEach(groupElm => {
          if (groupElm !== elm) {
            groupElm.checked = false;
          }
        });
      }

      // Remove group classes
      if (elm.matches('[data-class]')) {
        groupVals.forEach(className => {
          if (className !== value) {
            document.body.classList.remove(className);
          }
        });
      }
      // Disable group sheets
      else {
        const otherSheets = groupVals
          .map(val =>
            previewSheets.find(sheet => sheet.getAttribute('data-sheet') === val),
          )
          .filter(sheet => sheet && sheet.getAttribute('data-sheet') !== value);
        const disableSheets = otherSheets.length ? otherSheets : previewSheets;

        disableSheets.forEach(sheet => sheet.disabled = true);
      }
    }

    // Toggle active elms
    toggleElms.forEach(elm => {
      const value = elm.value;

      // Class toggle
      if (elm.matches('[data-class]')) {
        elm.checked = document.body.classList.contains(value);
      }
      // Sheet toggle
      else {
        const previewSheet = previewSheets.find(
          sheet => sheet.getAttribute('data-sheet') === value,
        );

        elm.checked = previewSheet && !previewSheet.disabled;
      }
    });

    toggleElms.forEach(elm => elm.addEventListener('change', handleChange));
  })();
</script>
