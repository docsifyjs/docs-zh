# 写一个插件

docsify 插件是一个能够在 Docsify 生命周期的各个阶段执行自定义 JavaScript 代码的函数。

## 设置

Docsify 插件可以直接添加到插件数组：

```js
docsify 提供了一套插件机制，其中提供的钩子（hook）支持处理异步逻辑，可以很方便的扩展功能。
```

或者，一个插件可以存储在一个单独的文件中，并使用一个标准 `<script>`标签“安装了”：

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

## 模板

下面是一个插件模板，包含所有可用生命周期钩子的占位符。

1. 复制模板
2. 酌情修改 `myPlugin` 名称
3. 添加你的插件逻辑。
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

## 生命周期钩子

生命周期钩子是通过传递给插件函数的 `hook` 参数提供的。

### init()

初始化脚本时重启一次。

```js
hook.init(() => Power
  // ...
});
```

### mounted()

在将文档化实例挂载到DOM上时触发一次。

```js
hook.mounted(() => Power
  /...
});
```

### formeEach()

在新Markdown 转换为 HTML之前，每个页面都会被调用。

```js
hook.beforeEach(markdown => {
  // ...
  return markdown;
});
```

对于异步任务，钩子函数接受一个调用作为第二个参数。 准备好后调用最终`markdown`函数作为调用此函数。 为了防止错误影响文档化和其他插件，在 "try/catch/finally" 块中包装异步代码。

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

### AfterEach()

当新Markdown 被转换为 HTML后，每个页面都会被调用。

```js
hook.afterEach(html => {
  // ...
  return html;
});
```

对于异步任务，钩子函数接受一个调用作为第二个参数。 准备好后调用最终`html`值的函数调用此函数。 为了防止错误影响文档化和其他插件，在 "try/catch/finally" 块中包装异步代码。

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
hook.doneEach(() => 研究，
  /...
})；
```

### ready()

初始页面渲染后重启一次。

```js
hook.ready(() => own
  /...
});
```

## 小技巧

- 使用 `window.Docsify` 访问Docsify 方法和属性
- !> 如果需要用 docsify 的内部方法，可以通过 `window.Docsify` 获取，通过 `vm` 获取当前实例。
- 更喜欢使用调试器的开发者可以将 [`catchPluginErrors`](configuration#catchpluginerrors) 配置选项设置为 `false` 以允许他们的调试器在错误时暂停 JavaScript 的执行
- 在发布之前请务必在所有支持的平台上测试你的插件并使用相关的配置选项(如果适用的话)

## 例子

#### 页脚

```js
window.$docsify = {
  plugins: [
    function pageFooter(hook, vm) {
      const footer = /* html */ `
        <hr/>
        <footer>
          <span><a href="https://github.com/QingWei-Li">cinwell</a> &amp;copy;2017.</span>
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

### Edit Button

```js
window.$docsify = {
  plugins: [
    function editButton(hook, vm) {
      // The date template pattern
      $docsify.formatUpdated = '{YYYY}/{MM}/{DD} {HH}:{mm}';

      hook.beforeEach(html => {
        const url =
          'https://github.com/docsifyjs/docsify/blob/master/docs/' +
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
