# 编写插件 :id=write-a-plugin

docsify 插件是一个能够在 Docsify 生命周期的各个阶段执行自定义 JavaScript 代码的函数。

## 设置 :id=setup

Docsify 插件可直接添加到 `plugins` 数组中：

```js
window.$docsify = {
  plugins: [
    function myPlugin1(hook, vm) {
      // ...
    },
    function myPlugin2(hook, vm) {
      // ...
    },
  ],
};
```

另外，插件可以存储在一个单独的文件中，并使用标准的 `<script>` 标签进行 "安装"：

```js
// docsify-plugin-myplugin.js

{
  function myPlugin(hook, vm) {
    // ...
  }

  // Add plugin to docsify's plugin array
  window.$docsify = window.$docsify || {};
  $docsify.plugins = [...($docsify.plugins || []), myPlugin];
}
```

```html
<script src="docsify-plugin-myplugin.js"></script>
```

## 模板 :id=template

下面是一个插件模板，其中包含所有可用生命周期钩子的占位符。

1. 复制模板
2. 酌情修改 `myPlugin` 名称
3. 添加你的插件逻辑
4. 删除未使用的生命周期钩子
5. 将文件保存为 `docsify-plugin-[name].js`
6. 使用标准 '<script>' 标签加载你的插件

```js
{
  function myPlugin(hook, vm) {
    // Invoked one time when docsify script is initialized
    hook.init(() => {
      // ...
    });

    // Invoked one time when the docsify instance has mounted on the DOM
    hook.mounted(() => {
      // ...
    });

    // Invoked on each page load before new markdown is transformed to HTML.
    // Supports asynchronous tasks (see beforeEach documentation for details).
    hook.beforeEach(markdown => {
      // ...
      return markdown;
    });

    // Invoked on each page load after new markdown has been transformed to HTML.
    // Supports asynchronous tasks (see afterEach documentation for details).
    hook.afterEach(html => {
      // ...
      return html;
    });

    // Invoked on each page load after new HTML has been appended to the DOM
    hook.doneEach(() => {
      // ...
    });

    // Invoked one time after rendering the initial page
    hook.ready(() => {
      // ...
    });
  }

  // Add plugin to docsify's plugin array
  window.$docsify = window.$docsify || {};
  $docsify.plugins = [myPlugin, ...($docsify.plugins || [])];
}
```

## 生命周期钩子 :id=lifecycle-hooks

生命周期钩子是通过 `hook` 参数传递给插件函数提供的。

### init()

docsify 脚本初始化时调用一次。

```js
hook.init(() => {
  // ...
});
```

### mounted()

当 docsify 实例挂载到 DOM 时调用一次。

```js
hook.mounted(() => {
  // ...
});
```

### beforeEach()

每次页面加载时，在新的 markdown 转换为 HTML 之前调用。

```js
hook.beforeEach(markdown => {
  // ...
  return markdown;
});
```

对于异步任务，钩子函数接受 `next` 回调作为第二个参数。 准备就绪后，使用最终的 `markdown` 值调用该函数。 为防止错误影响 docsify 和其他插件，请用 `try/catch/finally` 块封装异步代码。

```js
hook.beforeEach((markdown, next) => {
  try {
    // Async task(s)...
  } catch (err) {
    // ...
  } finally {
    next(markdown);
  }
});
```

### afterEach()

当新的 markdown 被转换为 HTML 后，每个页面都会被调用。

```js
hook.afterEach(html => {
  // ...
  return html;
});
```

对于异步任务，钩子函数接受 `next` 回调作为第二个参数。 准备就绪后，使用最终的 `html` 值调用该函数。 为防止错误影响 docsify 和其他插件，请用 `try/catch/finally` 块封装异步代码。

```js
hook.afterEach((html, next) => {
  try {
    // Async task(s)...
  } catch (err) {
    // ...
  } finally {
    next(html);
  }
});
```

### doneEach()

当新的 HTML 被添加到 DOM后，每个页面都会被调用。

```js
hook.doneEach(() => {
  // ...
});
```

### ready()

在渲染初始页面后调用一次。

```js
hook.ready(() => {
  // ...
});
```

## 小技巧 :id=tips

- 使用 `window.Docsify` 访问 Docsify 方法和属性
- 使用 `vm` 参数访问当前的 Docsify 实例
- 喜欢使用调试器的开发人员可以将 [`catchPluginErrors`](zh-cn/configuration#catchpluginerrors) 配置选项设置为 `false`，以允许调试器在出现错误时暂停 JavaScript 的执行
- 在发布之前，请确保在所有支持的平台上测试你的插件，并使用相关配置选项（如适用）进行测试

## 例子 :id=examples

#### 页脚 :id=page-footer

```js
window.$docsify = {
  plugins: [
    function pageFooter(hook, vm) {
      const footer = /* html */ `
        <hr/>
        <footer>
          <span><a href="https://github.com/QingWei-Li">cinwell</a> &copy;2017.</span>
          <span>Proudly published with <a href="https://github.com/docsifyjs/docsify" target="_blank">docsify</a>.</span>
        </footer>
      `;

      hook.afterEach(html => {
        return html + footer;
      });
    },
  ],
};
```

### 编辑按钮 (GitHub) :id=edit-button-github

```js
window.$docsify = {
  plugins: [
    function editButton(hook, vm) {
      // The date template pattern
      $docsify.formatUpdated = '{YYYY}/{MM}/{DD} {HH}:{mm}';

      hook.beforeEach(html => {
        const url =
          'https://github.com/docsifyjs/docsify/blob/main/docs/' +
          vm.route.file;
        const editHtml = '[📝 EDIT DOCUMENT](' + url + ')\n';

        return (
          editHtml +
          html +
          '\n----\n' +
          'Last modified {docsify-updated}' +
          editHtml
        );
      });
    },
  ],
};
```
