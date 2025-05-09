# 文件嵌入

从 Docsify 4.6 起可以嵌入任何类型的文件。

你可以嵌入这些文件作为视频、音频、iframes 或代码块，甚至 Markdown 文件也可以直接嵌入文档。

这是一个嵌入 Markdown 文件的例子。 你只需要这样做：

```markdown
[filename](../_media/example.md ':include')
```

`example.md` 文件的内容将会直接显示在这里：

[filename](../_media/example.md ":include")

你可以查看 [example.md](../_media/example.md ":ignore") 原始内容对比效果。

通常情况下，这样的语法将会被当作链接处理。但是在 docsify 里，如果你添加一个 `:include` 选项，它就会被当作文件嵌入。 你可以随意使用单引号或双引号。

外部链接也可以使用 - 只是替换目标。 如果你想要使用 gist URL，请查看[嵌入 gist](#embed-a-gist) 部分。

## 嵌入文件类型

目前，文件扩展名自动识别并以不同方式嵌入。

支持这些类型：

- **iframe** `.html`、`.htm`
- **markdown** `.markdown`、`.md`
- **audio** `.mp3`
- **video** `.mp4`、`.ogg`
- **code** 其它文件扩展

当然，你也可以强制指定类型。 例如，通过设置 `:type=code`，可将 Markdown 文件嵌入为代码块。

```markdown
[filename](../_media/example.md ':include :type=code')
```

你会看到：

[filename](../_media/example.md ":include :type=code")

## Markdown 与 YAML 元数据结合

Front Matter 通常在 Jekyl 等博客系统中使用，用于定义文档的元数据。 [front-matter.js](https://www.npmjs.com/package/front-matter) 包便于从文档中提取元数据(front matter)。

当使用 Markdown 时，YAML 元数据将从渲染的内容中删除。 在这种情况下不能使用属性。

```markdown
[filename](../_media/example-with-yaml.md ':include')
```

你将只获得内容

[filename](../_media/example-with-yaml.md ":include")

## 嵌入代码片段

有时你不想嵌入整个文件。 也许是因为你只需要几行，但你想在 CI 中编译和测试该文件。

```markdown
[filename](../_media/example.js ':include :type=code :fragment=demo')
```

在你的代码文件中，你需要用斜线 `/// [demo]` 包裹该片段（片段的前后都要有）。
或者你也可以使用 `### [demo]`。

示例：

[filename](../_media/example.js ":include :type=code :fragment=demo")

## 标签属性

如果你嵌入文件是一个 `iframe`、`audio` 或者 `video`，你可以给这些标签设置属性。

?> 注意，对于 `audio` 和 `video` 类型，默认情况下，对应添加 `controlls` 属性。 当你想要添加更多属性时，需要手动添加 `controls` 属性。

```md
[filename](../_media/example.mp4 ':include :type=video controls width=100%')
```

```markdown
[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')
```

[cinwell website](https://cinwell.com ":include :type=iframe width=100% height=400px")

你看到它了吗？ 你只需要直接写入属性。 每个标签有哪些属性建议你查看 [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)。

## 代码块高亮

嵌入任何类型的源代码文件，你可以指定高亮语言或自动标识。

```markdown
[](../_media/example.html ':include :type=code text')
```

⬇️

[](../_media/example.html ":include :type=code text")

?> 如何设置高亮？ 你可以查看[此处](zh-cn/language-highlight.md)。

## 嵌入 Gist

你可以将 Gist 作为 Markdown 内容或代码块嵌入。这是基于[嵌入文件](#embed-files)部分开头的方法，不过是嵌入一个原始的 Gist URL。

?> **无需**更改插件或应用程序配置即可运行。 事实上，即使你使用插件或修改配置来允许加载外部脚本，从 Gist 复制的 Embed `script` 标签也_无法_加载。

### 确定 Gist 的元数据

从查看 `gist.github.com` 上的 Gist 开始。 为了本指南的目的，我们使用这个 Gist：

- https://gist.github.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15

从 gist 中识别以下项目：

| 字段          | 示例                                 | 说明                                             |
| ----------- | ---------------------------------- | ---------------------------------------------- |
| **用户名**     | `anikethsaha`                      | Gist 的所有者。                                     |
| **Gist ID** | `c2bece08f27c4277001f123898d16a7c` | Gist 的标识符。 这在 gist 的生命周期内是固定的。                 |
| **文件名**     | `content.md`                       | 在 gist 中选择一个文件的名称。 即使是在单个文件的 gist 中也需要这样做才能嵌入。 |

你将需要这些来为目标文件建立 _raw gist URL_。 你会看到：

- `https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME`

下面是根据示例 Gist 举出的两个例子：

- https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md
- https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js

?> 或者，你可以直接点击 Gist 文件上的 _Raw_ 按钮获取原始 URL。 但如果你使用这种方法， 请务必**移除** `raw/` 和文件名之间的版本号，以便 URL 与上面的模式相匹配。 否则，当 Gist 更新时，你的嵌入式 Gist 将**不会**显示最新内容。

继续下面的一个部分，将 Gist 嵌入到 Docsify 页面上。

### 渲染 Gist 中的 Markdown 内容

这是将内容**无缝**嵌入到你的文档中的好方法，而不需要将别人引到外部链接。 这种方法非常适合在多个版本库的文档站点上重复使用安装说明要点。 这个方法与你的帐户或其他用户拥有的 Gist 同样有效。

格式：

```markdown
[LABEL](https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME ':include')
```

例如：

```markdown
[gist: content.md](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md ':include')
```

你会看到：

[gist: content.md](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/content.md ":include")

`LABEL` 可以是你想要的任何文本。 如果链接被破坏，它可以作为一个 _fallback_ 信息。所以在这里重复文件名是很有用的，万一你需要修复一个破坏的链接。 它还可以使嵌入的元素一目了然。

### 渲染 Gist 中的代码块

格式与上一节相同，但在 alt 文本中添加了 `:type=code`。 与[嵌入文件类型](#embedded-file-type)部分一样，语法高亮将从扩展名(如 `.js` 或 `.py`)中**推断**，所以你可以将 `type` 设置为 `code`。

格式：

```markdown
[LABEL](https://gist.githubusercontent.com/USERNAME/GIST_ID/raw/FILENAME ':include :type=code')
```

例如：

```markdown
[gist: script.js](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js ':include :type=code')
```

你会看到：

[gist: script.js](https://gist.githubusercontent.com/anikethsaha/f88893bb563bb7229d6e575db53a8c15/raw/script.js ":include :type=code")
