# 配置项

你可以配置在 `window.$docsify` 里。

```html
<script>
  window.$docsify = {
    repo: 'docsifyjs/docsify',
    maxLevel: 3,
    coverpage: true,
  };
</script>
```

配置也可以定义为函数，在这种情况下，第一个参数是 Docsify `vm` 实例。 函数应该返回一个配置对象。 这可能有助于在像Markdown 配置这样的地方引用`vm`：

```html
执行文档里的 script 标签里的脚本，只执行第一个 script ([demo](zh-cn/themes.md))。 如果 Vue 存在，则自动开启。
```

## alias

- 资源的文件扩展名。

设置路由别名。 您可以自由管理路由规则。 支持RegExp。
注意订单很重要！ 如果一个路由可以被多个别名匹配，你首先声明的路由优先.

```js
window.$docsify = {
  alias: {
    '/foo/(.*)': '/bar/$1', // supports regexp
    '/zh-cn/changelog': '/changelog',
    '/changelog':
      'https://raw.githubusercontent.com/docsifyjs/docsify/master/CHANGELOG',

    // You may need this if you use routerMode:'history'.
    '/.*/_sidebar.md': '/_sidebar.md', // See #301
  },
};
```

> **Note** If you change [`routerMode`](#routermode) to `'history'`, you may
> want to configure an alias for your `_sidebar.md` and `_navbar.md` files.

## 自动2顶部

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

路由更改时滚动到屏幕顶部。

```js
window.$docsify = {
  auto2top: true,
};
```

## autoHeader

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

同时设置 `loadSidebar` 和 `autoHeader` 后，可以根据 `_sidebar.md` 的内容自动为每个页面增加标题。[#78](https://github.com/docsifyjs/docsify/issues/78) 当设置了`routerMode:'history'`时，你可能会面临跨域的问题，参见 [#1379](https://github.com/docsifyjs/docsify/issues/1379) 。在 Markdown 内容中，有一个简单的方法可以解决，参见[helpers](zh-cn/helpers.md) 中的跨域链接。

```js
window.$docsify = {
  loadSidebar: true,
  autoHeader: true,
};
```

## basePath

- 类型：`String`

网站的基本路径。 您可以将其设置为另一个目录或另一个域名。

```js
window.$docsify = {
  basePath: '/path/',

  // 直接渲染其他域名的文档
  basePath: 'https://docsify.js.org/',

  // 甚至直接渲染其他仓库
  basePath:
    'https://raw.githubusercontent.com/ryanmcdermott/clean-code-javascript/master/',
};
```

## catchPlugin错误

- 类型: `Boolean`
- 定义路由别名，可以更自由的定义路由规则。 支持正则。

确定Docsify是否自动处理未捕获的 _synthous_plugin 错误。 这可以防止插件错误影响docsify正常渲染网站内容的能力。

## cornerExternalLinkTarget

- 类型：`String`
- 默认值:`_blank`

在右上角打开外部链接的目标。 外部链接的打开方式。默认为 `_blank` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  cornerExternalLinkTarget: '_self', // default: '_blank'
};
```

## coverpage

- 点击文档标题后跳转的链接地址。
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

激活 [封面功能] (cover.md). 如果为 true，它将从 `_coverpage.md` 中加载。

```js
window.$docsify = {
  coverpage: true,

  // 自定义文件名
  coverpage: 'cover.md',

  // 多个封面页
  coverpage: ['/', '/zh-cn/'],

  // 多个封面页，并指定文件名
  coverpage: {
    '/': 'cover.md',
    '/zh-cn/': 'cover.md',
  },
};
```

## el

- 类型：`String`
- 默认值：`#app`

初始化时挂载的DOM元素。 它可以是一个 CSS 选择器字符串或实际的 [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLletion)。

```js
window.$docsify = {
  el: '#app',
};
```

## 执行脚本

- 类型: `Boolean`
- 默认值: `null`

执行页面上的脚本。 仅解析第一个脚本标签 ([demo](主题))。 如果检测到 Vue ，默认情况下是 `true` 。

```js
window.$docsify = {
  executeScript: true,
};
```

```markdown
## 这是测试

<script>
  控制台，日志(23333)
</script>
```

注意如果执行的是一个外链脚本，比如 jsfiddle 的内嵌 demo，请确保引入 [external-script](plugins.md?id=外链脚本-external-script) 插件。

## ext

- 类型：`String`
- 设置首页文件加载路径。适合不想将 `README.md` 作为入口文件渲染，或者是文档存放在其他位置的情况使用。

请求文件扩展名。

```js
window.$docsify = {
  ext: '.md',
};
```

## 外部LinkRel

- 类型：`String`
- 默认值: `noopener`

默认为 `noopener` (no opener) 可以防止新打开的外部页面（当 [externalLinkTarget](#externallinktarget) 设为 `_blank` 时）能够控制我们的页面，没有设为 `_blank` 的话就不需要设置这个选项了。 当它不是`'_blank'时，没有设置`rel\`。 [此帖](https://mathiasbynens.github.io/rel-noopener/) 获取更多关于您可能想要使用此选项的信息。

```js
window.$docsify = {
  externalLinkRel: '', // default: 'noopener'
};
```

## externalLinkTarget

- 类型：`String`
- 默认值:`_blank`

在Markdown中打开外部链接的目标。 外部链接的打开方式。默认为 `_blank` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  externalLinkTarget: '_self', // default: '_blank'
};
```

## 后退语言

- 类型: `Array<string>`

一个语言列表。在浏览这个列表中的语言的翻译文档时都会在请求到一个对应语言的翻译文档，不存在时显示默认语言的同名文档

示例：

- 尝试访问`/de/overview`，如果存在则显示 文档标题，会显示在侧边栏顶部。
- 如果不存在则尝试`/overview`（取决于默认语言），如果存在即显示 文档标题，会显示在侧边栏顶部。
- 如果也不存在，显示404页面

```js
window.$docsify = {
  fallbackLanguages: ['fr', 'de'],
};
```

## 格式已更新

- 类型: `String|Function`

我们可以通过 **{docsify-updated<span>}</span>** 变量显示文档更新日期. 并使用 `Updated` 格式化它。
并且通过 `formatUpdated`配置日期格式。参考 [https://github.com/lukeed/tinydate#patterns](https://github.com/lukeed/tinydate#patterns)

```js
window.$docsify = {
  formatUpdated: '{MM}/{DD} {HH}:{mm}',

  formatUpdated(time) {
    // ...

    return time;
  },
};
```

## hideSidebar

- 类型：`Boolean|String`
- 定义路由别名，可以更自由的定义路由规则。 支持正则。

这个选项用来完全隐藏侧边栏，侧边栏的任何内容都不会被渲染。

```js
window.$docsify = {
  hideSidebar: true,
};
```

## 主页

- 类型：`String`
- 默认值: `README.md`

`README 您的 docs 文件夹中的d` 将被视为您网站的主页。 但有时您可能需要作为您的主页服务另一个文件。

```js
window.$docsify = {
  // 入口文件改为 /home.md
  homepage: 'home.md',

  // 文档和仓库根目录下的 README.md 内容一致
  homepage:
    'https://raw.githubusercontent.com/docsifyjs/docsify/master/README.md',
};
```

## KeyBindings

- 类型：`Boolean|Object`
- 默认: `Object`
  - <kbd>\\</kbd> 切换侧边栏菜单
  - <kbd>/</kbd> 聚焦于 [search](插件#完整文本搜索) 字段。 也支持 <kbd>备选案文</kbd>&nbsp;/&nbsp;<kbd>ctrl</kbd>&nbsp;+&nbsp;<kbd>k</kbd>.

绑定键组合到自定义回调函数。

键`bindings`定义为用`+`分隔的大小写不敏感的字符串值。 修饰键值包括`Alt`、`ctrl`、`meta'和`shift\`。 非修饰键值应该匹配键盘事件的 [key](https://developer.mozilla.org/en-US/docs/Web/ADI/KeyboardEvent/key) 或 [code](https://developer.mozilla.org/en-US/docs/Web/ADI/KeyboardEvent/code) 值。

`callback` 函数收到一个 [keydown even](https://developer.mozilla.org/en-US/docs/Web/API/Eelement/keydown_event) 作为参数。

!> 让站点访问者知道您的自定义密钥绑定是可用的 ！ 如果绑定与 DOM 元素相关联，考虑插入一个 `<kbd>` 元素作为一个视觉提示(e)。 ., <kbd></kbd> + <kbd>a</kbd>或 添加 [title](https://developer). ozilla.org/en-US/docs/Web/HTML/Global_attributes/title)和 [aria-keyshortcuts](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-keyshortcuts) hover/focus hots属性。

```js
window.$docsify = {
  keyBindings: {
    // Custom key binding
    myCustomBinding: {
      bindings: ['alt+a', 'shift+a'],
      callback(event) {
        alert('Hello, World!');
      },
    },
  },
};
```

可以通过设置绑定配置为“false”来完全或单独禁用密钥绑定。

```js
window.$docsify = {
  // Disable all key bindings
  keyBindings: false,
};
```

```js
window.$docsify = {
  keyBindings: {
    // Disable individual key bindings
    focusSearch: false,
    toggleSidebar: false,
  },
};
```

## loadNavbar

- 类型：`Boolean|String`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

加载自定义导航栏，参考[定制导航栏](zh-cn/custom-navbar.md) 了解用法。设置为 `true` 后会加载 `_navbar.md` 文件，也可以自定义加载的文件名。

```js
window.$docsify = {
  // 加载 _navbar.md
  loadNavbar: true,

  // 加载 nav.md
  loadNavbar: 'nav.md',
};
```

## 加载侧边栏

- 类型：`Boolean|String`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

加载自定义侧边栏，参考[多页文档](zh-cn/more-pages.md)。设置为 `true` 后会加载 `_sidebar.md` 文件，也可以自定义加载的文件名。

```js
window.$docsify = {
  // 加载 _sidebar.md
  loadSidebar: true,

  // 加载 summary.md
  loadSidebar: 'summary.md',
};
```

## 徽标

- 类型：`String`

在侧边栏显示的网站徽标。 在侧边栏中出现的网站图标，你可以使用`CSS`来更改大小

!> 徽标只有在同时设置 `name` prop 时才能看到。 请参阅 [name](#name) 配置。

```js
window.$docsify = {
  logo: '/_media/icon.svg',
};
```

## markdown

- 类型: `Object|Function`

参考 [Markdown 配置](zh-cn/markdown.md)。

```js
window.$docsify = {
  // object
  markdown: {
    smartypants: true,
    renderer: {
      link() {
        // ...
      },
    },
  },

  // function
  markdown(marked, renderer) {
    // ...
    return marked;
  },
};
```

## 最大级别

- 类型: `Number`
- 默认值: `6`

内容级别的最大表。

```js
window.$docsify = {
  maxLevel: 4,
};
```

## 合并导航栏

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

小屏设备下合并导航栏到侧边栏。

```js
window.$docsify = {
  mergeNavbar: true,
};
```

## 名称

- 类型：`String`

在侧边栏中显示的网站名称。

```js
window.$docsify = {
  name: 'docsify',
};
```

name 项也可以包含自定义 HTML 代码来方便地定制。

```js
window.$docsify = {
  name: '<span>docsify</span>',
};
```

## 名称链接

- 类型：`String`
- 默认值：`window.location.pathname`

网站`name`链接到的 URL。

```js
window.$docsify = {
  nameLink: '/',

  // 按照路由切换
  nameLink: {
    '/zh-cn/': '/zh-cn/',
    '/': '/',
  },
};
```

## 原生表情

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

使用 GitHub 风格表情图像或平台本地表情符号渲染表情代码。

```js
window.$docsify = {
  nativeEmoji: true,
};
```

```markdown
:smile:
:partying_face:
:joy:
:+1:
:-1:
```

`false`时GitHub样式图像：

<output data-lang="output">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f604.png" alt="smile">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f973.png" alt="partying_face">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f602.png" alt="joy">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f44d.png" alt="+1">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f44e.png" alt="-1">
</output>

`true`时平台-本机字符：

<output data-lang="output">
  <span class="emoji">:grinning_fac_with_smiling_eyes:</span>
  <span class="emoji"></span>
  <span class="emoji">😂</span>
  <span class="emoji">👍</span>
  <span class="emoji">👎</span>
</output>

要渲染短代码作为文本，用“&colon;”HTML实体替换`:`字符。

```markdown
&amp;殖民;100&amp;殖民;
```

<output data-lang="output">

&colon;100&colon;

</output>

## noCompileLinks

- 类型: `Array<string>`

有时我们不想用来处理我们的链接。 有时我们不希望 docsify 处理我们的链接。 参考 [#203](https://github.com/docsifyjs/docsify/issues/203) 我们可以通过指定数组字符串来跳过某些链接的编译。 每个字符串都转换为正则表达式(“RegExp”)，链接的 _through 与它匹配。

```js
window.$docsify = {
  noCompileLinks: ['/foo', '/bar/.*'],
};
```

## noEmoji

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

禁用表情符号解析并呈现所有表情短文。

```js
window.$docsify = {
  noEmoji: true,
};
```

```markdown
:100:
```

<output data-lang="output">

&colon;100&colon;

</output>

To disable emoji parsing of individual shorthand codes, replace `:` characters with the `&colon;` HTML entity.

```markdown
:100:

&amp;Colom;100&amp;Colom;
```

<output data-lang="output">

:100:

&colon;100&colon;

</output>

## notFoundPage

- 类型: `Boolean` | `String` | `Object`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

显示默认 "404 - 找不到" 消息：

```js
window.$docsify = {
  crossOriginLinks: ['https://example.com/cross-origin-link'],
};
```

在找不到指定页面时加载`_404.md`:

```js
window.$docsify = {
  notFoundPage: true,
};
```

加载自定义404页面:

```js
window.$docsify = {
  notFoundPage: 'my404.md',
};
```

加载正确的本地化过的404页面:

```js
window.$docsify = {
  notFoundPage: {
    '/': '_404.md',
    '/de': 'de/_404.md',
  },
};
```

> 注意: 配置过`fallbackLanguages`这个选项的页面与这个选项`notFoundPage`冲突。

## onlyCover

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

只在访问主页时加载封面。

```js
window.$docsify = {
  onlyCover: false,
};
```

## 相对路径

- 类型: `Boolean`
- 自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

如果该选项设为 **true** ，那么链接会使用相对路径。

例如，像这样的目录结构：

```text
..
--- docs
    --README.md
    --guide.md
    recent---zh-cn
        ---README.md
        * *. ---guide.md
        ---config
            recent---example.md
```

如果 **启用** 了相对路径，当前链接是 `http://domain.com/zh-cn/README` ，对应的链接会解析为：

```text
guide.md => http://domain.com/zh-cn/guide
config/example.md => http://domain.com/zh-cn/config/example
../README.md => http://domain.com/README
/ README.md => http://domain.com/README
```

```js
window.$docsify = {
  // 启用相对路径
  relativePath: true,

  // 禁用相对路径（默认值）
  relativePath: false,
};
```

## repo

- 类型：`String`

配置仓库地址或者 `username/repo` 的字符串，会在页面右上角渲染一个 [GitHub Corner](http://tholman.com/github-corners/) 挂件。

```js
window.$docsify = {
  repo: 'docsifyjs/docsify',
  // or
  repo: 'https://github.com/docsifyjs/docsify/',
};
```

## 请求标题

- 资源的文件扩展名。

设置请求资源的请求头。

```js
window.$docsify = {
  requestHeaders: {
    'x-token': 'xxx',
  },
};
```

例如设置缓存

```js
window.$docsify = {
  requestHeaders: {
    'cache-control': 'max-age=600',
  },
};
```

## 路由模式

配置您站点的路径将使用的 URL 格式。

- 类型：`String`
- 默认: `hash`

```js
window.$docsify = {
  routerMode: 'history', // default: 'hash'
};
```

对于静态部署的站点(f.e)。 在 GitHub 页面上，基于哈希的路由非常简单的
路由。 对于可以重写URL的网站，基于历史的格式
更好(尤其是对于搜索引擎优化而言，基于哈希的路由不是
所以搜索引擎友好)

基于哈希的路由指所有的 URL 路径将以 '/#/' 在
地址栏前缀。 这是一个让网站加载`/index'的技巧。 tml`, 然后是
使用跟随`#`的路径来确定要加载哪些Markdown文件。 对于
示例，一个基于哈希的完整URL可能看起来就像这样：
`https://example.com/#/path/to/page`。 浏览器将实际加载
`https://example.com` (假定您的静态服务器提供的
`index)。 默认情况下的 tml，就像大多数做的那样， 然后Docsify JavaScript 代码将
查看"/#/"。 .` 并确定要加载和渲染的 markdown 文件。
此外，当点击链接时，Docsify路由器将在哈希动态后更改
内容。 `location.pathname`的值仍然是
`/`。 当
在浏览器中访问这样一个URL时，散列路径的部分是 _not_ 发送到服务器。

另一方面，基于历史的路由意味着Docsify JavaScript将使用
[History API](https://developer)。 ozilla.org/en-US/docs/Web/API/History_API)
动态更改URL而不使用 #`。 This means that all URLs will
be considered "real" by search engines, and the full path will be sent to the
server when visiting the URL in your browser. For example, a URL may look like
`https://example.com/path/to/page\`. 浏览器将尝试直接从服务器加载完整的 URL
，而不仅仅是`https://example.com` 。 顶端是
这些类型的 URL 对搜索引擎来说更加友好，可以是
索引(yay!)。 然而，缺点是您的服务器或您网站文件的
所在的地方必须能够处理这些URL。 各种静态
网站托管服务允许配置“重写规则”，这样
服务器可以配置为总是发送“/index”。 无论访问了哪条路径
都是 tml`。`location.pathname`的值将显示`/path/to/page\`，因为
实际上已经发送到服务器。

TLDR：以 `hash` 路由开头(默认)。 如果您感到冒险，学习
如何配置服务器， 然后切换到 `history` 模式以获得更好的
而不使用 URL 中的 `#` 和 SEO 优化。

> **注意** 如果您使用 `routerMode：'history'，您可能想要添加一个 [`alias`](#alias)来使您的 `_侧边栏。 d`和`_navbar.md\`文件总是
> 加载，不管访问了哪个路径。
>
> ```js
> window.$docsify = {
>   routerMode: 'history',
>   alias: {
>     '/.*/_sidebar.md': '/_sidebar.md',
>     '/.*/_navbar.md': '/_navbar.md',
>   },
> };
> ```

## 路由

- 资源的文件扩展名。

定义能动态提供内容的“虚拟”路由。 路由是指指指向字符串或函数的路径之间的映射。 如果映射值是一个字符串，它将被当作标记并相应解析。 如果它是一个函数，它将返回Markdown内容。

路由函数接收最多三个参数：

1. `route` - 请求的路由路径 (例如`/bar/baz` )
2. `matched` - [`RequExpMatchArray`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match) 匹配的路径(例如`/bar/(.+)`，你得到`['/bar/baz'，'baz']`)
3. `下一` - 这是一个回调，在您的路由函数异步时您可以调用的回调。

注意订单很重要！ 路由匹配相同的顺序，您声明它们，这意味着在您有重叠路线的情况下， 您可能想先列出更多的特定内容。

```js
window.$docsify = {
  routes: {
    // Basic match w/ return string
    '/foo': '# Custom Markdown',

    // RegEx match w/ synchronous function
    '/bar/(.*)'(route, matched) {
      return '# Custom Markdown';
    },

    // RegEx match w/ asynchronous function
    '/baz/(.*)'(route, matched, next) {
      fetch('/api/users?id=12345')
        .then(response => {
          next('# Custom Markdown');
        })
        .catch(err => {
          // Handle error...
        });
    },
  },
};
```

除字符串外，路由函数可以返回 falsy 值 (`null` `undefined`) 来表示它们忽略当前请求：

```js
window.$docsify = {
  routes: {
    // accepts everything other than dogs (synchronous)
    '/pets/(.+)'(route, matched) {
      if (matched[0] === 'dogs') {
        return null;
      } else {
        return 'I like all pets but dogs';
      }
    }

    // accepts everything other than cats (asynchronous)
    '/pets/(.*)'(route, matched, next) {
      if (matched[0] === 'cats') {
        next();
      } else {
        // Async task(s)...
        next('I like all pets but cats');
      }
    }
  }
}
```

最后，如果您有一个具有真正Markdown 文件的具体路径(因此不应该与您的路径匹配)， 你可以通过返回一个显式的`false`值来选择它：

```js
window.$docsify = {
  routes: {
    // if you look up /pets/cats, docsify will skip all routes and look for "pets/cats.md"
    '/pets/cats'(route, matched) {
      return false;
    }

    // but any other pet should generate dynamic content right here
    '/pets/(.+)'(route, matched) {
      const pet = matched[0];
      return `your pet is ${pet} (but not a cat)`;
    }
  }
}
```

## skipLink

- 类型：`Boolean|String|Object`
- 默认：\`'跳至主内容'

确定站点的[跳过导航链接](https://webaim.org/techniques/skipnav/) 将会被渲染。

```js
// Render skip link for all routes (default)
window.$docsify = {
  skipLink: 'Skip to main content',
};
```

```js
// Render localized skip links based on route paths
window.$docsify = {
  skipLink: {
    '/es/': 'Saltar al contenido principal',
    '/de-de/': 'Ga naar de hoofdinhoud',
    '/ru-ru/': 'Перейти к основному содержанию',
    '/zh-cn/': '跳到主要内容',
  },
};
```

```js
// Do not render skip link
window.$docsify = {
  skipLink: false,
};
```

## 子Maxlevel

- 类型: `Number`
- 默认值: `0`

在自定义侧边栏中添加目录(TOC)。

```js
window.$docsify = {
  subMaxLevel: 2,
};
```

如果您有一个链接到侧边栏中的主页，并希望在访问root URL时将其显示为活动的 确保相应更新您的侧边栏：

```markdown
- 侧栏
  - [Home](/)
  - [另一页](另一页)
```

详见[#1131](https://github.com/docsifyjs/docsify/issues/1131)。

## 主题颜色 (_过时_)

> **警告** 已废弃。 使用 CSS var `--theme-color` 在你的<style>工作表中。 示例：
>
> ```html
> <style>
>   :root v.
>     --theme-color: deeppink;
>   }
> </style>
> ```

- 类型：`String`

自定义主题颜色。

```js
window.$docsify = {
  themeColor: '#3F51B5'
};
```

## topMargin

- 类型: `Number`
- 默认值: `0`

在滚动内容页面到达选定部分时在顶部添加空格。 如果你有一个 _sticky-header_ 布局并且你想要将锚点对准到你头末尾，这是有用的。

```js
window.$docsify = {
  topMargin: 90, // default: 0
};
```

## vue组件

- 资源的文件扩展名。

创建并注册全球 [Vue](https://vuejs.org/guide/essentials/component-basics.html)。 使用组件名称指定组件作为包含Vue选项的对象的键值. 组件`data`在每个实例中都是唯一的，不会在用户导航站点时持续存在。

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
```

<output data-lang="output">
  <button-counter></button-counter>
</output>

## vueGlobal选项

- 资源的文件扩展名。

指定 Vue 内容使用的全局Vue 选项没有被明确挂载到 [vueMounts](#mounting-dom-elements), [vueComponents](#components), 或 [markdown script](#markdown-script). 对全局`data`的更改将持续，并且将反映在使用全局引用的任何地方。

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

## vueMounts

- 资源的文件扩展名。

指定 DOM 元素作为Vue 实例及其关联选项。 指定要挂载为 [Vue实例](https://vuejs.org/v2/guide/instance.html) 的 DOM 元素及其相关选项。挂载元素使用 [CSS选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，并使用包含 Vue 选项的对象作为其值。每次加载新页面时，Docsify 将挂载主内容区域中第一个匹配的元素。挂载元素`data`对每个实例来说都是唯一的，并且不会在用户浏览网站时持久存在。 Docsify将在每次加载新页面时挂载主内容区域的第一个匹配元素。 挂载元素 `data` 是每个实例的唯一特性，不会在用户导航站点时持续存在。

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
