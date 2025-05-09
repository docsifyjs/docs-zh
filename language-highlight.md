# 代码高亮

## Prism

Docsify 使用 [Prism](https://prismjs.com) 在代码块内进行语法高亮显示。 Prism 默认支持以下语言（也可提供额外的[语言支持](#language-support)）：

- Markup：HTML、XML、SVG、MathML、SSML、Atom、RSS
- CSS
- C-like
- JavaScript

要启用语法高亮，请使用反标（` ``` `）创建一个标记符代码块，并在第一行指定一个 [language](https://prismjs.com/#supported-languages)（例如`html`、`css`、`js`）：

````text
```html
<p>This is a paragraph</p>
<a href="//docsify.js.org/">Docsify</a>
```
````

````text
```css
p {
  color: red;
}
```
````

````text
```js
function add(a, b) {
  return a + b;
}
```
````

上面的 markdown 将被渲染为：

```html
<p>This is a paragraph</p>
<a href="//docsify.js.org/">Docsify</a>
```

```css
p {
  color: red;
}
```

```js
function add(a, b) {
  return a + b;
}
```

## 语言支持 :id=language-support

通过加载 Prism [语法文件](https://cdn.jsdelivr.net/npm/prismjs@1/components/)，可支持其他[语言](https://prismjs.com/#supported-languages)：

!> 必须在 Docsify 之后加载 Prism 语法文件。

```html
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-docker.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-git.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-java.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-jsx.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-markdown.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-rust.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-sql.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-swift.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-typescript.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-yaml.min.js"></script>
```

## 主题支持 :id=theme-support

Docsify 的官方[主题](zh-cn/themes)与 Prism 语法高亮主题兼容。

!> Prism 主题必须在 Docsify 主题之后加载。

```html
<!-- Light and dark mode -->
<link
  rel="stylesheet"
  href="//cdn.jsdelivr.net/npm/prism-themes@1/themes/prism-one-light.min.css"
/>
```

主题可在浅色和/或深色模式下使用

```html
<!-- Dark mode only -->
<link
  rel="stylesheet"
  media="(prefers-color-scheme: dark)"
  href="//cdn.jsdelivr.net/npm/prism-themes@1/themes/prism-one-dark.min.css"
/>

<!-- Light mode only -->
<link
  rel="stylesheet"
  media="(prefers-color-scheme: light)"
  href="//cdn.jsdelivr.net/npm/prism-themes@1/themes/prism-one-light.min.css"
/>
```

以下 Docsify [主题属性](zh-cn/themes#theme-properties) 默认覆盖 Prism 主题样式：

```text
--border-radius
--font-family-mono
--font-size-mono
```

要使用 Prism 主题中指定的值，请将所需的主题属性设置为 `unset`：

<!-- prettier-ignore -->

```html
<style>
  :root {
    --border-radius   : unset;
    --font-family-mono: unset;
    --font-size-mono  : unset;
  }
</style>
```

## 动态内容

可以使用 Prism 的 [`highlightElement()`](https://prismjs.com/docs/Prism.html#.highlightElement) 方法高亮显示动态生成的代码块：

```js
const code = document.createElement('code');
code.innerHTML = "console.log('Hello World!')";
code.setAttribute('class', 'language-javascript');
Prism.highlightElement(code);
```
