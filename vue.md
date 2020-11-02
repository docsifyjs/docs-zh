# 兼容 Vue

你可以直接在 Markdown 文件里写 Vue 代码，它将被执行。我们可以用它写一些 Vue 的 Demo 或者示例代码。


## 基础用法

在 `index.html` 里引入 Vue。

```html
<script src="//cdn.jsdelivr.net/npm/vue"></script>
<script src="//cdn.jsdelivr.net/npm/docsify"></script>

<!-- 或者使用压缩版文件  -->
<script src="//cdn.jsdelivr.net/npm/vue/dist/vue.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

接着就可以愉快地在 Markdown 里写 Vue 了。默认会执行 `new Vue({ el: '#main' })` 创建示例。

*README.md*

````markdown
# Vue 介绍

`v-for` 的用法

```html
<ul>
  <li v-for="i in 10">{{ i }}</li>
</ul>
```

<ul>
  <li v-for="i in 10">{{ i }}</li>
</ul>
````

当然你也可以手动初始化 Vue，这样你可以自定义一些配置。

*README.md*

```markdown
# Vue 的基本用法

<div id="main">hello {{ msg }}</div>

<script>
  new Vue({
    el: '#main',
    data: { msg: 'Vue' }
  })
</script>
```

!> 一个 Markdown 文件里只有第一个 `script` 标签内的内容会被执行。

## 搭配 Vuep 写 Playground

[Vuep](https://github.com/QingWei-Li/vuep) 是一个提供在线编辑和预览效果的 Vue 组件，搭配 docsify 可以直接在文档里写 Vue 的示例代码，支持 Vue component spec 和 JSX。

*index.html*

```html
<!-- 引入 CSS 文件 -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/vuep/dist/vuep.css">

<!-- 引入 JavaScript 文件 -->
<script src="//cdn.jsdelivr.net/npm/vue"></script>
<script src="//cdn.jsdelivr.net/npm/vuep"></script>
<script src="//cdn.jsdelivr.net/npm/docsify"></script>

<!-- 或引入压缩版文件 -->
<script src="//cdn.jsdelivr.net/npm/vue/dist/vue.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/vuep/dist/vuep.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

*README.md*
```markdown
# Vuep 使用

<vuep template="#example"></vuep>

<script v-pre type="text/x-template" id="example">
  <template>
    <div>Hello, {{ name }}!</div>
  </template>

  <script>
    module.exports = {
      data: function () {
        return { name: 'Vue' }
      }
    }
  </script>
</script>
```


?> 具体效果参考 [Vuep 文档](https://qingwei-li.github.io/vuep/)。
