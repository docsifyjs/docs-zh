# 语言高亮

Docsify 使用 [Prism](https://prismjs.com) 突出显示您页面中的代码块。 棱镜默认支持以下语言：

- Markup - `markup`, `html`, `xml`, `svg`, `mathml`, `ssml`, `atom`, `rss`
- CSS - `css`
- Clike - `clike`
- JavaScript - `javascript`, `js`

[添加额外的语法支持](https://prismjs.com/#supported-languages)需要通过CDN添加相应的[语法文件](https://cdn.jsdelivr.net/npm/prismjs@1/components/) :

```html
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
```

!> This `<script>` tag must be placed after the docisfy `<script>` to work.

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

## 突出显示动态内容

代码块[动态从 javascript](https://docsify.js.org/#/configuration?id=executescript) 可以用类似于 `Prism.highlightElement` 的方法突出显示：

```javascript
const code = document.createElement('code');
code.innerHTML = "console.log('Hello World!')";
code.setAttribute('class', 'lang-javascript');
Prism.highlightElement(code);
```
