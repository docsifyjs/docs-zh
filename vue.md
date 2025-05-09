# 兼容 Vue

Docsify 允许 [Vue.js](https://vuejs.org) 内容直接添加到你的 markdown 页面。 这可以极大地简化与数据的工作并将反应添加到你的站点。

Vue [template syntax](https://vuejs.org/guide/essentials/template-syntax) 可以用来将动态内容添加到你的页面。 当使用 [data](#data)、[computed properties](#computed-properties)、[methods](#methods) 和 [lifecycle hooks](#lifecycle-hooks) 时，Vue 内容会变得更加有趣。 这些选项可以指定为 [全局选项](#global-options) 或 DOM [mounts](#mounts) 和 [components](#components)。

## 设置

若要开始，请将 Vue.js 添加到你的 `index.html` 文件。 为你的站点选择合适的生产版本或开发版本，以获得有用的控制台警告和 [Vue.js devtools](https://github.com/vuejs/vue-devtools) 支持。

```html
<!-- Production -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.prod.js"></script>

<!-- Development -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.js"></script>
```

## 模板语法 :id=template-syntax

Vue [template syntax](https://vuejs.org/guide/essentials/template-syntax) 提供了一些有用的功能，例如支持 [JavaScript expressions](https://vuejs.org/guide/essentials/template-syntax.html#using-javascript-expressions) 和 Vue [directives](https://vuejs.org/guide/essentials/template-syntax.html#directtives) 用于循环和条件渲染。

```markdown
<!-- Hide in docsify, show elsewhere (e.g. GitHub) -->
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

[在 GitHub 上查看输出](https://github.com/docsifyjs/docsify/blob/develop/docs/vue.md#template-syntax)

## 代码块 :id=code-blocks

默认情况下，Docsify 忽略代码块中的 Vue 模板语法：

````markdown
```
{{ message }}
```
````

要在代码块中处理 Vue 模板语法，请将代码块封装在带有 `v-template` 属性的元素中：

````markdown
<div v-template>

```
{{ message }}
```

</div>
````

## 数据 :id=data

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
<!-- Show message in docsify, show "{{ message }}" elsewhere (e.g. GitHub)  -->
{{ message }}

<!-- Show message in docsify, hide elsewhere (e.g. GitHub)  -->
<p v-text="message"></p>
```

<!-- prettier-ignore-end -->

<output data-lang="output">
  <p>{{ message }}</p>

  <p v-text="message"></p>
</output>

[在 GitHub 上查看输出](https://github.com/docsifyjs/docsify/blob/develop/docs/vue.md#data)

## 计算属性 :id=computed-properties

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

## 方法 :id=methods

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

## 生命周期钩子 :id=lifecycle-hooks

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

## 全局选项 :id=global-options

使用 `vueGlobalOptions` 来指定用于使用 Vue 内容的全局 Vue 选项，这些内容没有被明确挂载 [vueMounts](#mounts)、[vueComponents](#components) 或 [markdown 脚本](#markdown-script)。 对全局 `data` 的更改将持续存在，并在使用全局引用的任何地方得到反映。

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
  <button @click="count += 1">+</button>
  {{ count }}
  <button @click="count -= 1">-</button>
</p>
```

<output data-lang="output">
  <p>
    <button @click="count += 1">+</button>
    {{ count }}
    <button @click="count -= 1">-</button>
  </p>
</output>

请注意当多个全局计数器呈现时的行为：

<output data-lang="output">
  <p>
    <button @click="count += 1">+</button>
    {{ count }}
    <button @click="count -= 1">-</button>
  </p>
</output>

对一个计数器的更改会影响到两个计数器。 这是因为两个实例都引用了相同的全局 `count` 值。 现在，导航到一个新页面，然后返回到本节，看看在页面加载之间对全局数据所做的更改是如何持续的。

## 挂载 :id=mounts

使用 `vueMounts` 指定要挂载为 Vue 实例的 DOM 元素及其相关选项。 挂载元素是使用 [CSS 选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，包含 Vue 选项的对象作为值来指定的。 每次加载新页面时，Docsify 都会在主内容区域挂载第一个匹配元素。 挂载元素 `data` 是每个实例的唯一特性，不会在用户导航站点时持续存在。

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
  <button @click="count += 1">+</button>
  {{ count }}
  <button @click="count -= 1">-</button>
</div>
```

<output id="counter">
  <button @click="count += 1">+</button>
  {{ count }}
  <button @click="count -= 1">-</button>
</output>

## 组件 :id=components

使用 `vueComponents` 创建和注册全局 [Vue components](https://vuejs.org/guide/essentials/component-basics.html)。 指定组件时，以组件名称为键，以包含 Vue 选项的对象为值。 组件 `data` 在每个实例中都是唯一的，不会在用户导航站点时持续存在。

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

## Markdown 脚本 :id=markdown-script

Vue 内容可以使用 markdown 页面中的 `<script>` 标签进行挂载。

!> 只执行 markdown 文件中的第一个 `<script>` 标签。 你可以直接在 markdown 文件里写 Vue 代码，它将被执行。我们可以用它写一些 Vue 的 Demo 或者示例代码。

```html
<script>
  Vue.createApp({
    // Options...
  }).mount('#example');
</script>
```

## 技术说明 :id=technical-notes

- 每次加载页面时，Docsify 都会按以下顺序处理 Vue 内容：
  1. 执行 markdown `<script>`
  2. 注册全局 `vueComponents`
  3. 挂载 `vueMounts`
  4. 自动挂载未挂载的 `vueComponents`
  5. 使用 `vueGlobalOptions` 自动挂载未挂载的 Vue 模板语法
- 自动加载 Vue 内容时，docsify 将加载 markdown 中包含模板语法或组件的每个顶级元素。 例如，在下面的 HTML 中，顶层的 `<p>`、`<my-component />` 和 `<div>` 元素将被挂载。
  ```html
  <p>{{ foo }}</p>
  <my-component />
  <div>
    <span>{{ bar }}</span>
    <some-other-component />
  </div>
  ```
- Docsify 不会加载现有的 Vue 实例或包含现有 Vue 实例的元素。
- Docsify 会在每次页面加载前自动销毁/卸载其创建的所有 Vue 实例。
