# 兼容 Vue

Docsify允许 [Vue.js](https://vuejs.org) 内容直接添加到您的Markdown页面。 这可以极大地简化与数据的工作并将反应添加到您的站点。

Vue [template syntax](https://vuejs.org/guide/essentials/template-syntax) 可以用来将动态内容添加到您的页面。 当使用[data](#data)、[computed properties](#computed-properties)、[methods](#methods)和[lifecycle hooks](#lifecycle-hooks)时，Vue内容会变得更加有趣。这些选项可以作为[全局选项](#global-options)或在DOM中的[mounts](#mounts)和[component](#components)来指定。 这些选项可以指定为 [全局选项] (#global-options) 或 DOM [mounts](#mounts) 和 [components](#components)。

## 设置

若要开始，请将 Vue.js 添加到您的 `index.html` 文件。 为你的站点选择合适的生产版本或开发版本，以获得有用的控制台警告和 [Vue.js devtools](https://github.com/vuejs/vue-devtools) 支持。

```html
<!-- Production -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.prod.js"></script>

<!-- Development -->
<script src="//cdn.jsdelivr.net/npm/vue@3/dist/vue.global.js"></script>
```

## 模板语法

Vue [template syntax](https://vuejs.org/guide/essentials/template-syntax) 提供了一些有用的功能，例如支持[JavaScript expressions](https://vuejs.org/guide/essentials/template-syntax.html#using-javascript-expressions) 和 Vue [directives](https://vuejs.org/guide/essentials/template-syntax.html#directtives) 用于循环和条件渲染。

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

## 代码块

默认情况下，Docsify 忽略代码块中的 Vue 模板语法：

````markdown
```
{{ message}}
```
````

若要在代码块中处理Vue 模板语法，用`v-template`的属性把代码块换成一个元素：

````markdown
<div v-template>

```
{{ message}}
```

</div>
````

## 数据

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

[在GitHub上查看输出](https://github.com/docsifyjs/docsify/blob/develop/docs/vue.md#data)

## 计算的属性

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

## 方法

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

## 生命周期钩子

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

## 全局选项

使用 `vueGlobalOptions` 来指定用于使用 Vue 内容的全局Vue 选项，这些内容没有被明确挂载 [vueMounts](#mounts), [vueComponents](#components), 或 [markdown 脚本](#markdown-script). 对全局`data`的更改将持续，并且将反映在使用全局引用的任何地方。

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

对一个计数器所作的更改影响到两个计数。 这是因为两个实例都引用了相同的全局`count`值。 现在，导航到一个新的页面并返回到这个部分，看看如何在页面加载之间对全局数据的更改会持续下去。

## 挂载

使用 `vueMounts` 指定要挂载为Vue 实例及其相关选项的DOM元素。 使用`vueMounts`来指定要挂载为 [Vue实例](https://vuejs.org/v2/guide/instance.html) 的DOM元素及其相关选项。挂载元素使用 [CSS选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，并使用一个包含Vue选项的对象作为其值。每次加载新页面时，Docsify将挂载主内容区域中第一个匹配的元素。挂载元素`data`对每个实例来说都是唯一的，并且在用户浏览网站时不会持久。 Docsify将在每次加载新页面时挂载主内容区域的第一个匹配元素。 挂载元素 `data` 是每个实例的唯一特性，不会在用户导航站点时持续存在。

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

## 组件

使用 `vueComponents` 创建和注册全局[Vue components](https://vuejs.org/guide/essentials/component-basics.html)。 使用组件名称指定组件作为包含Vue选项的对象的键值. 组件`data`在每个实例中都是唯一的，不会在用户导航站点时持续存在。

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

## Markdown 脚本

Vue内容可以使用 Markdown 页面中的`<script>`标签进行挂载。

!> 只有 Markdown 文件中的第一个`<script>`标签会被执行。如果你想使用脚本标签挂载多个Vue实例，所有实例必须挂载在Markdown的第一个脚本标签内。 你可以直接在 Markdown 文件里写 Vue 代码，它将被执行。我们可以用它写一些 Vue 的 Demo 或者示例代码。

```html
<script>
  Vue.createApp({
    // Options...
  }).mount('#example');
</script>
```

## 技术说明

- 每个页面加载时按以下顺序对应处理 Vue 内容：
  1. 执行 markdown `<script>`
  2. 注册全局`vueComponents`
  3. 挂载 `vueMounts`
  4. 自动挂载`vueComponents`
  5. 使用 `vueGlobalOptions` 自动挂载 Vue 模板语法
- 自动挂载 Vue 内容，文档化将挂载您Markdown中包含模板语法或组件的每个顶级元素。 例如，在下面的 HTML 中，顶层的<p>`、`<my-component />`和`<div>\`元素将被挂载。
  ```html
  <p>{{ foo }}</p>
  <my-component />
  <div>
    <span>{{ bar }}</span>
    <some-other-component />
  </div>
  ```
- Docsify 将不会挂载现有的 Vue 实例或包含现有的 Vue 实例的元素。
- Docsify 将自动销毁/卸载它在每个页面加载之前创建的所有Vue 实例。
