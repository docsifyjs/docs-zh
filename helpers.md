# 文档助手

docsify 扩展了一些 Markdown 语法，可以让文档更易读。

> 注意：对于特殊代码语法案例来说，最好是将它们放在代码的后端里，以避免配置或表情发生任何冲突。

## 强调内容

重要内容如：

```markdown
!> **时间** 是钱，我的朋友！
```

渲染为：

!> **时间** 是钱，我的朋友！

## 普通提示

一般提示如：

```markdown
?> _TODO_单位测试
```

渲染为：

?> _TODO_单位测试

## 忽略编译链接

有时候我们会把其他一些相对路径放到链接上，你必须告诉 docsify 你不需要编译这个链接。 例如： 例如：

```md
[link](/demo/)
```

它将被编译为 `<a href="/#/demo/">link</a>` 并将加载 `/demo/README.md`. 可能你想跳转到 `/demo/index.html`。

现在你可以做到这一点

```md
[link](/demo/':ignore')
```

即将会得到 `<a href="/demo/">link</a>` html 代码。不要担心，你仍然可以为链接设置标题。 跨域链接

```md
[link](/demo/':nove title')

<a href="/demo/" title="title">链接</a>
```

## 设置链接的 target 属性

```md
[link](/demo ':target=_blank')
[link](/demo2 ':target=_self')
```

## 禁用链接

```md
[link](/demo ':禁用')
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
- 条形图
- [x] baz
- []bam <~没有工作
  - [ ] 自行车
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

![logo](https://docsify.js.org/_media/icon.svg ":size=50x100")
![logo](https://docsify.js.org/_media/icon.svg ":size=100")
![logo](https://docsify.js.org/_media/icon.svg ":size=10%")

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
这对于在细节元素中渲染Markdown内容是有用的。

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
