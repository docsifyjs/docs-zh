# Markdown 配置

**docsify** 使用 [marked](https://github.com/markedjs/marked) 作为其 Markdown 解析器。 你可以通过自定义 `renderer` 来定制如何将 Markdown 内容渲染为 HTML：

```js
window.$docsify = {
  markdown: {
    smartypants: true,
    renderer: {
      link() {
        // ...
      },
    },
  },
};
```

?> 完整配置参数参考 [marked 文档](https://marked.js.org/#/USING_ADVANCED.md)

你可以完全自定义解析规则。

```js
window.$docsify = {
  markdown(marked, renderer) {
    // ...

    return marked;
  },
};
```

## 支持 mermaid

!> 目前 docsify 不支持异步 mermaid 渲染（最新的 mermaid 版本是 `v9.3.0`）。

```js
//  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.css">
//  <script src="//cdn.jsdelivr.net/npm/mermaid@9.3.0/dist/mermaid.min.js"></script>

let num = 0;
mermaid.initialize({ startOnLoad: false });

window.$docsify = {
  markdown: {
    renderer: {
      code({ text, lang }) {
        if (lang === 'mermaid') {
          return /* html */ `
            <div class="mermaid">${mermaid.render(
              'mermaid-svg-' + num++,
              text,
            )}</div>
          `;
        }
        return this.origin.code.apply(this, arguments);
      },
    },
  },
};
```
