# 兼容 Vue

你可以直接在 Markdown 文件里写 Vue 代码，它将被执行。我们可以用它写一些 Vue 的 Demo 或者示例代码。

首先，将 Vue[2.x](https://vuejs.org) 或 [3.x](https://v3.vuejs.org) 添加到你的`index.html`文件中。

为你的站点选择合适的生产版本或开发版本，以获得有用的控制台警告和 [Vue.js devtools](https://github.com/vuejs/vue-devtools) 支持。

#### Vue 2.x

```html
<!-- Production -->
<script src="//cdn.jsdelivr.net/npm/vue@2/dist/vue.min.js"></script>

<!-- Development -->
<script src="//cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
```

#### Vue 3.x

```html
<!-- Production -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.prod.js"></script>

<!-- Development -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.js"></script>
```

## 模板语法

Vue[模板语法](https://vuejs.org/v2/guide/syntax.html) 用于创建动态内容。无需额外的配置，这种语法提供了一些有用的功能，如支持 [JavaScript表达式](https://vuejs.org/v2/guide/syntax.html#Using-JavaScript-Expressions) 和 Vue[指令](https://vuejs.org/v2/guide/syntax.html#Directives) 的循环和条件渲染。

```markdown
<!-- 在docsify中隐藏，在其他地方显示（如GitHub）。 -->
<p v-if="false">Text for GitHub</p>

<!-- Sequenced content (i.e. loop)-->
<ul>
  <li v-for="i in 3">Item {{ i }}</li>
</ul>

<!-- JavaScript expressions -->
<p>2 + 2 = {{ 2 + 2 }}</p>
```

<output data-lang="output">
  <p v-if="false">Text for GitHub</p>

  <ul>
    <li v-for="i in 3">Item {{ i }}</li>
  </ul>

  <p>2 + 2 = {{ 2 + 2 }}</p>
</output>

[在GitHub上查看输出](https://github.com/docsifyjs/docsify/blob/develop/docs/vue.md#template-syntax)

当使用[data](#data)、[computed properties](#computed-properties)、[methods](#methods)和[lifecycle hooks](#lifecycle-hooks)时，Vue内容会变得更加有趣。这些选项可以作为[全局选项](#global-options)或在DOM中的[mounts](#mounts)和[component](#components)来指定。

### Data

```js
{
  data() {
    return {
      message: 'Hello, World!'
    };
  }
}
```

<!-- prettier-ignore-start -->
```markdown
<!-- 在docsify中显示消息，在其他地方显示 "{{ message }}"（例如GitHub） -->
{{ message }}

<!-- 在docsify中显示消息，在其他地方隐藏（例如GitHub） -->
<p v-text="message"></p>

<!-- 在docsify中显示消息，在其他地方显示 text（例如GitHub） -->
<p v-text="message">Text for GitHub</p>
```
<!-- prettier-ignore-end -->

<output data-lang="output">

{{ message }}

  <p v-text="message"></p>
  <p v-text="message">Text for GitHub</p>
</output>

[在GitHub上查看输出](https://github.com/docsifyjs/docsify/blob/develop/docs/vue.md#data)

### Computed properties

```js
{
  computed: {
    timeOfDay() {
      const date = new Date();
      const hours = date.getHours();

      if (hours < 12) {
        return 'morning';
      }
      else if (hours < 18) {
        return 'afternoon';
      }
      else {
        return 'evening'
      }
    }
  },
}
```

```markdown
Good {{ timeOfDay }}!
```

<output data-lang="output">

Good {{ timeOfDay }}!

</output>

### Methods

```js
{
  data() {
    return {
      message: 'Hello, World!'
    };
  },
  methods: {
    hello() {
      alert(this.message);
    }
  },
}
```

```markdown
<button @click="hello">Say Hello</button>
```

<output data-lang="output">
  <p><button @click="hello">Say Hello</button></p>
</output>

### Lifecycle Hooks

```js
{
  data() {
    return {
      images: null,
    };
  },
  created() {
    fetch('https://api.domain.com/')
      .then(response => response.json())
      .then(data => (this.images = data))
      .catch(err => console.log(err));
  }
}

// API response:
// [
//   { title: 'Image 1', url: 'https://domain.com/1.jpg' },
//   { title: 'Image 2', url: 'https://domain.com/2.jpg' },
//   { title: 'Image 3', url: 'https://domain.com/3.jpg' },
// ];
```

```markdown
<div style="display: flex;">
  <figure style="flex: 1;">
    <img v-for="image in images" :src="image.url" :title="image.title">
    <figcaption>{{ image.title }}</figcaption>
  </figure>
</div>
```

<output data-lang="output">
  <div style="display: flex;">
    <figure v-for="image in images" style="flex: 1; text-align: center;">
      <img :src="image.url">
      <figcaption>{{ image.title }}</figcaption>
    </figure>
  </div>
</output>

## Global options

使用`vueGlobalOptions`来指定 [Vue options](https://vuejs.org/v2/api/#Options-Data) ，用于未明确挂载[vueMounts](#mounts)、[vueComponents](#components)或[markdown脚本](#markdown-script)的Vue内容。对全局`data`的更改将持续存在，并反映在任何使用全局引用的地方。

```js
window.$docsify = {
  vueGlobalOptions: {
    data() {
      return {
        count: 0,
      };
    },
  },
};
```

```markdown
<p>
  <button @click="count -= 1">-</button>
  {{ count }}
  <button @click="count += 1">+</button>
</p>
```

<output data-lang="output">
  <p>
    <button @click="count -= 1">-</button>
    {{ count }}
    <button @click="count += 1">+</button>
  </p>
</output>

请注意当多个全局计数器呈现时的行为：

<output data-lang="output">
  <p>
    <button @click="count -= 1">-</button>
    {{ count }}
    <button @click="count += 1">+</button>
  </p>
</output>

对一个计数器的更改会影响两个计数器。这是因为两个实例都引用了相同的全局`count`值。现在，导航到一个新的页面，并返回本节，查看对全局数据的更改如何在页面加载之间持久化。

## Mounts

使用`vueMounts`来指定要挂载为 [Vue实例](https://vuejs.org/v2/guide/instance.html) 的DOM元素及其相关选项。挂载元素使用 [CSS选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，并使用一个包含Vue选项的对象作为其值。每次加载新页面时，Docsify将挂载主内容区域中第一个匹配的元素。挂载元素`data`对每个实例来说都是唯一的，并且在用户浏览网站时不会持久。

```js
window.$docsify = {
  vueMounts: {
    '#counter': {
      data() {
        return {
          count: 0,
        };
      },
    },
  },
};
```

```markdown
<div id="counter">
  <button @click="count -= 1">-</button>
  {{ count }}
  <button @click="count += 1">+</button>
</div>
```

<output id="counter">
  <button @click="count -= 1">-</button>
  {{ count }}
  <button @click="count += 1">+</button>
</output>

## Components

使用`vueComponents`创建和注册全局[Vue组件](https://vuejs.org/v2/guide/components.html) 。组件是以组件名称为键，以包含Vue选项的对象为值来指定的。组件`data`对每个实例来说都是唯一的，并且在用户浏览网站时不会持久存在。

```js
window.$docsify = {
  vueComponents: {
    'button-counter': {
      template: `
        <button @click="count += 1">
          You clicked me {{ count }} times
        </button>
      `,
      data() {
        return {
          count: 0,
        };
      },
    },
  },
};
```

```markdown
<button-counter></button-counter>
<button-counter></button-counter>
```

<output data-lang="output">
  <button-counter></button-counter>
  <button-counter></button-counter>
</output>

## Markdown script

Vue内容可以使用 Markdown 页面中的`<script>`标签进行挂载。

!> 只有 Markdown 文件中的第一个`<script>`标签会被执行。如果你想使用脚本标签挂载多个Vue实例，所有实例必须挂载在Markdown的第一个脚本标签内。

```html
<!-- Vue 2.x  -->
<script>
  new Vue({
    el: '#example',
    // Options...
  });
</script>
```

```html
<!-- Vue 3.x  -->
<script>
  Vue.createApp({
    // Options...
  }).mount('#example');
</script>
```

## Technical Notes

- Docsify processes Vue content in the following order on each page load:
  1. Execute markdown `<script>`
  1. Register global `vueComponents`
  1. Mount `vueMounts`
  1. Auto-mount unmounted `vueComponents`
  1. Auto-mount unmounted Vue template syntax using `vueGlobalOptions`
- When auto-mounting Vue content, docsify will mount each top-level element in your markdown that contains template syntax or a component. For example, in the following HTML the top-level `<p>`, `<my-component />`, and `<div>` elements will be mounted.
  ```html
  <p>{{ foo }}</p>
  <my-component />
  <div>
    <span>{{ bar }}</span>
    <some-other-component />
  </div>
  ```
- Docsify will not mount an existing Vue instance or an element that contains an existing Vue instance.
- Docsify will automatically destroy/unmount all Vue instances it creates before each page load.

## 说明

- Docsify 在每次加载页面时按以下顺序处理Vue内容：
  1.执行 Markdown `<script>`
  1.注册全局 `vueComponents`
  1.挂载 `vueMounts`
  1.自动挂载未安装的 `vueComponents`
  1.使用 `vueGlobalOptions` 自动挂载未安装的Vue模板语法
- 自动挂载Vue内容时，docsify将挂载Markdown中包含模板语法或组件的每个顶级元素。例如，在以下HTML中，将安装顶级`<p>`，`<my-component />`和`<div>`元素。
  ```html
  <p>{{ foo }}</p>
  <my-component />
  <div>
    <span>{{ bar }}</span>
    <some-other-component />
  </div>
  ```
- Docsify将不会挂载现有Vue实例或包含现有Vue实例的元素。
- Docsify将在每次加载页面之前自动销毁/卸载其创建的所有Vue实例。
