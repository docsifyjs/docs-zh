# 文档助手

docsify 扩展了一些 Markdown 语法，可以让文档更易读。

## 强调内容

适合显示重要的提示信息，语法为 `!> 内容`。

```markdown
!> 一段重要的内容，可以和其他 **Markdown** 语法混用。
```

!> 一段重要的内容，可以和其他 **Markdown** 语法混用。

## 普通提示

普通的提示信息，比如写 TODO 或者参考内容等。

```markdown
?> _TODO_ 完善示例
```

?> _TODO_ 完善示例

## 忽略编译链接

有时候我们会把其他一些相对路径放到链接上，你必须告诉 docsify 你不需要编译这个链接。 例如：

```md
[link](/demo/)
```

它将被编译为 `<a href="/#/demo/">link</a>` 并将加载 `/demo/README.md`. 可能你想跳转到 `/demo/index.html`。

现在你可以做到这一点

```md
[link](/demo/ ':ignore')
```

即将会得到 `<a href="/demo/">link</a>` html 代码。不要担心，你仍然可以为链接设置标题。

```md
[link](/demo/ ':ignore title')

<a href="/demo/" title="title">link</a>
```

## 设置链接的 target 属性

```md
[link](/demo ':target=_blank')
[link](/demo2 ':target=_self')
```

## 禁用链接

```md
[link](/demo ':disabled')
```

## 跨域链接

只有当你同时设置了 `routerMode: 'history'` 和 `externalLinkTarget: '_self'` 时，你需要为这些跨域链接添加这个配置。

```md
[example.com](https://example.com/ ':crossorgin')
```

## Github 任务列表

```md
- [ ] foo
- bar
- [x] baz
- [] bam <~ not working
  - [ ] bim
  - [ ] lim
```

- [ ] foo
- bar
- [x] baz
- [] bam <~ not working
  - [ ] bim
  - [ ] lim

## 图片处理

### 缩放

```md
![logo](https://docsify.js.org/_media/icon.svg ':size=WIDTHxHEIGHT')
![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')

<!-- 支持按百分比缩放 -->

![logo](https://docsify.js.org/_media/icon.svg ':size=10%')
```

![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')
![logo](https://docsify.js.org/_media/icon.svg ':size=10%')

### 设置图片的 Class

```md
![logo](https://docsify.js.org/_media/icon.svg ':class=someCssClass')
```

### 设置图片的 ID

```md
![logo](https://docsify.js.org/_media/icon.svg ':id=someCssId')
```

## 设置标题的 id 属性

```md
### 你好，世界！ :id=hello-world
```

## html 标签中的 Markdown

你需要在 html 和 Markdown 内容中插入空行。
当你需要在 details 元素中渲染 Markdown 时很有用。

```markdown
<details>
<summary>自我评价（点击展开）</summary>

- Abc
- Abc

</details>
```

<details>
<summary>自我评价（点击展开）</summary>

- Abc
- Abc

</details>

Markdown 内容也可以被 html 标签包裹。

```markdown
<div style='color: red'>

- listitem
- listitem
- listitem

</div>
```

<div style='color: red'>

- Abc
- Abc

</div>
