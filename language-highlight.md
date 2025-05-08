# 代码高亮

Docsify 使用 [Prism](https://prismjs.com) 突出显示您页面中的代码块。 Prism 默认支持以下语言：

- Markup - `markup`, `html`, `xml`, `svg`, `mathml`, `ssml`, `atom`, `rss`
- CSS - `css`
- Clike - `clike`
- JavaScript - `javascript`, `js`

[添加额外的语法支持](https://prismjs.com/#supported-languages)需要通过CDN添加相应的[语法文件](https://cdn.jsdelivr.net/npm/prismjs@1/components/)：

```html
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
```

要使用语法高亮，需要在代码块第一行添加对应的[语言声明](https://prismjs.com/#supported-languages)，示例如下:

````
```html
<p>This is a paragraph</p>
<a href="//docsify.js.org/">Docsify</a>
```

```bash
echo "hello"
```

```php
function getAdder(int $x): int 
{
    return 123;
}
```
````

上面的Markdown 将被渲染为：

```html
<p>This is a paragraph</p>
<a href="//docsify.js.org/">Docsify</a>
```

```bash
echo "hello"
```

```php
function getAdder(int $x): int 
{
    return 123;
}
```

## 动态内容高亮

通过 [javascript 动态创建](/#/zh-cn/configuration?id=executescript)的代码块，可以使用 `Prism.highlightElement` 方法进行高亮：

```javascript
var code = document.createElement("code");
code.innerHTML = "console.log('Hello World!')";
code.setAttribute("class", "lang-javascript");
Prism.highlightElement(code);
```
