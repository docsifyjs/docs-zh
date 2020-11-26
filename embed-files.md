# 文件嵌入

docsify 4.6 开始支持嵌入任何类型的文件到文档里。你可以将文件当成 `iframe`、`video`、`audio` 或者 `code block`，如果是 Markdown 文件，甚至可以直接插入到当前文档里。

这是一个嵌入 Markdown 文件的例子。

```markdown
[filename](../_media/example.md ':include')
```

`example.md` 文件的内容将会直接显示在这里

[filename](../_media/example.md ':include')

你可以查看 [example.md](../_media/example.md ':ignore') 原始内容对比效果。

通常情况下，这样的语法将会被当作链接处理。但是在 docsify 里，如果你添加一个 `:include` 选项，它就会被当作文件嵌入。

## 嵌入的类型

当前，嵌入的类型是通过文件后缀自动识别的，这是目前支持的类型：

* **iframe** `.html`, `.htm`
* **markdown** `.markdown`, `.md`
* **audio** `.mp3`
* **video** `.mp4`, `.ogg`
* **code** other file extension

当然，你也可以强制设置嵌入类型。例如你想将 Markdown 文件当作一个 `code block` 嵌入。
```markdown
[filename](../_media/example.md ':include :type=code')
```

你会看到：

[filename](../_media/example.md ':include :type=code')

## 嵌入代码片段
有时候你并不想嵌入整个文件，可能你只想要其中的几行代码，但你还要在 CI 系统中编译和测试该文件。

```markdown
[filename](../_media/example.js ':include :type=code :fragment=demo')
```

在你的代码文件中，你需要用斜线 `/// [demo]` 包裹该片段（片段的前后都要有）。
你也可以使用 `### [demo]` 来包裹。

示例：

[filename](../_media/example.js ':include :type=code :fragment=demo')

## 标签属性

如果你嵌入文件是一个 `iframe`、`audio` 或者 `video`，你可以给这些标签设置属性。

```markdown
[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')
```

[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')

看见没？你只需要直接写属性就好了，每个标签有哪些属性建议你查看 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)。

## 代码块高亮

如果是嵌入一个代码块，你可以设置高亮的语言，或者让它自动识别。这里是手动设置高亮语言

```markdown
[](../_media/example.html ':include :type=code text')
```

⬇️

[](../_media/example.html ':include :type=code text')

?> 如何高亮代码？你可以查看[这份文档](zh-cn/language-highlight.md)。

## 嵌入Gist

你可以将 Gist 作为 Markdown 内容或代码块嵌入。这是基于[嵌入文件](#embed-files)部分开头的方法，不过是嵌入一个原始的 Gist URL。

?> 这里**不需要**插件或修改配置来使其工作。事实上，即使你使用插件或修改配置来允许加载外部脚本，从 Gist 复制的 "Embed" `script`标签也无法加载。

### 确定Gist的元数据

从查看`gist.github.com`上的 Gist 开始。在本指南中，我们使用这个 Gist：

- https://gist.github.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15

从 Gist 中找出以下内容：

| 字段         | 示例                               | 说明                                                                |
| ------------ | ---------------------------------- | ------------------------------------------------------------------- |
| **Username** | `anikethsaha`                      | Gist 的作者                                                         |
| **Gist ID**  | `c2bece08f27c4277001f123898d16a7c` | Gist 的标识符。该标识在 Gist 的有效期内是固定的                     |
| **Filename** | `content.md`                       | 在 Gist 中选择一个文件名。即使是单文件的 Gist，也需要这样做才能嵌入 |

你将需要这些来为目标文件建立 _raw gist URL_ 。它的格式如下：

- `https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME`

下面是根据示例 Gist 举出的两个例子：

- https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md
- https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js

?> 另外你也可以直接点击 Gist 文件上的 _Raw_ 按钮来获取原始 URL。但是如果你使用这种方法，请确保**删除**`raw/`和文件名之间的修订号，这样 URL 就会与上面的模式一致。否则当更新 Gist 时，你嵌入的 Gist 将**不会**显示最新的内容。

继续下面的一个部分，将 Gist 嵌入到 Docsify 页面上。

### 渲染 Gist 中的 Markdown 内容

这是一个很好的方法，可以将内容**无缝**地嵌入到你的文档中，而不需要将别人发送到外部链接。这种方法很适合在多个仓库的文档网站上重复使用一个 Gist，比如安装说明。这种方法同样适用于您的账户或其他用户拥有的 Gist。

格式：

```markdown
[LABEL](https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME ':include')
```

例如：

```markdown
[gist: content.md](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md ':include')
```

你会看到：

[gist: content.md](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md ':include')

`LABEL`可以是任何你想要的文本。如果链接被破坏，它可以作为一个 _fallback_ 信息。所以在这里重复文件名是很有用的，万一你需要修复一个破坏的链接。它还可以使嵌入的元素一目了然。

### 渲染 Gist 中的代码块

格式与上一节相同，但是在alt文本中添加了`:type=code`。与[嵌入的类型](#embedded-file-type)部分一样，语法高亮将从扩展名(如`.js`或`.py`)中**推断**，所以你可以将`type`设置为`code`。

格式：

```markdown
[LABEL](https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME ':include :type=code')
```

例如：

```markdown
[gist: script.js](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js ':include :type=code')
```

你会看到：

[gist: script.js](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js ':include :type=code')
