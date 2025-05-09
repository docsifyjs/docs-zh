# 封面

通过设置 `coverpage` 为 **true** 来开启渲染封面功能。 参见 [coverpage configuration](zh-cn/configuration#coverpage)。

## 基本用法

设置 `coverpage` 为 **true**, 并创建 `_coverpage.md` ：

```js
window.$docsify = {
  coverpage: true,
};
```

```markdown
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify

> A magical documentation site generator

- Simple and lightweight
- No statically built HTML files
- Multiple themes

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)
```

## 定制化

封面页可使用[主题属性](zh-cn/theme#theme-properties)进行自定义：

<!-- prettier-ignore -->

```css
:root {
  --cover-bg         : url('path/to/image.png');
  --cover-bg-overlay : rgba(0, 0, 0, 0.5);
  --cover-color      : #fff;
  --cover-title-color: var(--theme-color);
  --cover-title-font : 600 var(--font-size-xxxl) var(--font-family);
}
```

或者，可以在封面页面 markdown 中指定背景颜色或图像。

```markdown
<!-- background color -->

![color](#f0f0f0)
```

```markdown
<!-- background image -->

![](_media/bg.png)
```

## 封面作为首页

通常，封面页和主页同时出现。 当然，你也可以用[`onlyCover`](zh-cn/configuration#onlycover)选项分离封面。

## 多个封面

如果你的文档网站是多语言的，或许你需要设置多个封面。

例如你的文档目录结构如下

```text
.
└── docs
    ├── README.md
    ├── guide.md
    ├── _coverpage.md
    └── zh-cn
        ├── README.md
        └── guide.md
        └── _coverpage.md
```

现在，你可以设置

```js
window.$docsify = {
  coverpage: ['/', '/zh-cn/'],
};
```

或者指定具体的文件名

```js
window.$docsify = {
  coverpage: {
    '/': 'cover.md',
    '/zh-cn/': 'cover.md',
  },
};
```
