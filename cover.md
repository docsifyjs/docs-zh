# 封面

通过设置 `coverpage` 为 **true** 来激活封面功能。 通过设置 `coverpage` 参数，可以开启渲染封面的功能。具体用法见[配置项#coverpage](configuration.md#coverpage)。

## 基本用法

设置 `coverpage` 为 **true**, 并创建 `_coverpage.md` ：

```html
<!-- index.html -->

<script>
  window.$docsify = {
    coverpage: true,
  };
</script>
<script src="//cdn.jsdelivr.net/npm/docsify@5/dist/docsify.min.js"></script>
```

```markdown
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> 一个神奇的文档网站生成器。

- 简单、轻便 (压缩后 ~21kB)
- 无需生成 html 文件
- 众多主题

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)
```

## 自定义背景

默认情况下随机生成背景颜色。 您可以自定义背景颜色或背景图像：

```markdown
<!-- _coverpage.md -->

# docsify <small>3.5</small>

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#quick-start)

<!-- 背景图片 -->

![](_media/bg.png)

<!-- 背景色 -->

![color](#f0f0f0)
```

## 封面作为首页

通常，封面页和主页同时出现。 通常封面和首页是同时出现的，当然你也是当封面独立出来通过设置[onlyCover 选项](zh-cn/configuration.md#onlycover)。

## 多个封面

如果你的文档网站是多语言的，或许你需要设置多个封面。

例如你的文档目录结构如下

```text
..
--- docs
    ---README.md
    --guide.md
    - *. --_coverpage.md
    ------zh-cn
        - --- README.md
        recent--- guide.md
        - --_coverpage.md
```

现在，您可以设置

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
