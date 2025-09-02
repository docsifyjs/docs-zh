# 文档助手

docsify 扩展了一些 Markdown 语法，可以让文档更易读。

> 注意：对于特殊的代码语法，最好将其放在代码的反斜线内，以避免与配置或表情符号发生冲突。

## 标注

Docsify 支持 [GitHub 风格](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts) 标注（也称为“警告”或“警报”）。

<!-- prettier-ignore -->

> [!CAUTION]
> **Caution** callouts communicate negative potential consequences of an action.

<!-- prettier-ignore -->

> [!IMPORTANT]
> **Important** callouts communicate information necessary for users to succeed.

<!-- prettier-ignore -->

> [!NOTE]
> **Note** callouts communicate information that users should take into account.

<!-- prettier-ignore -->

> [!TIP]
> **Tip** callouts communicate optional information to help a user be more successful.

<!-- prettier-ignore -->

> [!WARNING]
> **Warning** callouts communicate potential risks user should be aware of.

**Markdown**

<!-- prettier-ignore -->

```markdown
> [!CAUTION]
> **Caution** callouts communicate negative potential consequences of an action.

> [!IMPORTANT]
> **Important** callouts communicate information necessary for users to succeed.

> [!NOTE]
> **Note** callouts communicate information that users should take into account.

> [!TIP]
> **Tip** callouts communicate optional information to help a user be more successful.

> [!WARNING]
> **Warning** callouts communicate potential risks user should be aware of.
```

### 传统风格 ⚠️ :id=legacy-style-

以下 Docsify v4 标注语法已被弃用，并将在未来版本中删除。

!> Legacy **Important** callouts are deprecated.

?> Legacy **Tip** callouts are deprecated.

**Markdown**

```markdown
!> Legacy **Important** callouts are deprecated.

?> Legacy **Tip** callouts are deprecated.
```

## 链接属性

### disabled

```markdown
[link](/demo ':disabled')
```

### href

有时候我们会把其他一些相对路径放到链接上，你必须告诉 docsify 你不需要编译这个链接。 例如：

```markdown
[link](/demo/)
```

它将被编译为 `<a href="/#/demo/">link</a>` 并将加载 `/demo/README.md`。 可能你想跳转到 `/demo/index.html`。

现在你可以做到这一点

```markdown
[link](/demo/ ':ignore')
```

你会得到 `<a href="/demo/">link</a>` html 代码。 不要担心，你仍然可以为链接设置标题。

```markdown
[link](/demo/ ':ignore title')

<a href="/demo/" title="title">link</a>
```

### target

```markdown
[link](/demo ':target=_blank')
[link](/demo2 ':target=_self')
```

## 任务清单

```markdown
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

## 图片

### 类名

```markdown
![logo](https://docsify.js.org/_media/icon.svg ':class=someCssClass')

<!-- Multiple class names -->

![logo](https://docsify.js.org/_media/icon.svg ':class=someCssClass :class=anotherCssClass')
```

### ID

```markdown
![logo](https://docsify.js.org/_media/icon.svg ':id=someCssId')
```

### 大小

```markdown
![logo](https://docsify.js.org/_media/icon.svg ':size=WIDTHxHEIGHT')
![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')

<!-- 支持按百分比缩放 -->

![logo](https://docsify.js.org/_media/icon.svg ':size=10%')
```

![logo](https://docsify.js.org/_media/icon.svg ":size=50x100")
![logo](https://docsify.js.org/_media/icon.svg ":size=100")
![logo](https://docsify.js.org/_media/icon.svg ":size=10%")

## 设置标题的 id 属性

```markdown
### 你好，世界！ :id=hello-world
```

## HTML 标签中的 Markdown

你需要在 html 和 markdown 内容之间插入空格。
这对于在 details 元素中呈现 markdown 内容非常有用。

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

- listitem
- listitem
- listitem

</div>
