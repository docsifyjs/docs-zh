# 配置项 :id=configuration

你可以通过将 `window.$docsify` 定义为一个对象来配置 Docsify：

```html
<script>
  window.$docsify = {
    repo: 'docsifyjs/docsify',
    maxLevel: 3,
    coverpage: true,
  };
</script>
```

配置也可以定义为函数，在这种情况下，第一个参数是 Docsify `vm` 实例。 该函数应该返回一个配置对象。 这对于在 markdown 配置等地方引用 `vm` 非常有用：

```html
<script>
  window.$docsify = function (vm) {
    return {
      markdown: {
        renderer: {
          code(code, lang) {
            // ... use `vm` ...
          },
        },
      },
    };
  };
</script>
```

## alias

- 类型：`Object`

设置路由别名。 你可以自由管理路由规则。 支持 RegExp。
请注意，顺序很重要！ 如果一个路由可以被多个别名匹配，那么你首先声明的路由优先。

```js
window.$docsify = {
  alias: {
    '/foo/(.*)': '/bar/$1', // supports regexp
    '/zh-cn/changelog': '/changelog',
    '/changelog':
      'https://raw.githubusercontent.com/docsifyjs/docsify/main/CHANGELOG',

    // You may need this if you use routerMode:'history'.
    '/.*/_sidebar.md': '/_sidebar.md', // See #301
  },
};
```

> **注意** 如果将 [`routerMode`](#routermode) 更改为 `'history'`，可能
> 需要为 `_sidebar.md` 和 `_navbar.md` 文件配置别名。

## auto2top

- 类型：`Boolean`
- 默认：`false`

更改路由时，滚动到屏幕顶部。

```js
window.$docsify = {
  auto2top: true,
};
```

## autoHeader

- 类型：`Boolean`
- 默认：`false`

如果同时启用了 `loadSidebar` 和 `autoHeader` 功能，则对于 `_sidebar.md`中的每个链接，都会在将其转换为 HTML 之前为页面预置一个标题，但前提是该页面尚未包含 H1 标题。

参见 [#78](https://github.com/docsifyjs/docsify/issues/78)。

```js
window.$docsify = {
  loadSidebar: true,
  autoHeader: true,
};
```

## basePath

- 类型：`String`

网站的基本路径。 你可以将其设置为另一个目录或另一个域名。

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

## catchPluginErrors

- 类型：`Boolean`
- 默认：`true`

决定 Docsify 是否应自动处理未捕获的 _synchronous_ 插件错误。 这可以防止插件错误影响 docsify 正常渲染网站内容的能力。

## cornerExternalLinkTarget

- 类型：`String`
- 默认：`'_blank'`

右上角的外部链接打开方式。 默认为 `'_blank'` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  cornerExternalLinkTarget: '_self', // default: '_blank'
};
```

## coverpage

- 类型：`Boolean|String|String[]|Object`
- 默认：`false`

激活[封面功能](zh-cn/cover.md)。 如果为 true，它将从 `_coverpage.md` 中加载。

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
- 默认：`'#app'`

要在初始化时挂载的 DOM 元素。 它可以是一个 CSS 选择器字符串或实际的 [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLletion)。

```js
window.$docsify = {
  el: '#app',
};
```

## executeScript

- 类型：`Boolean`
- 默认：`null`

执行页面上的脚本。 仅解析第一个脚本标签（[demo](zh-cn/themes)）。 如果检测到 Vue ，默认情况下是 `true` 。

```js
window.$docsify = {
  executeScript: true,
};
```

```markdown
## This is test

<script>
  console.log(2333)
</script>
```

注意，如果运行的是外部脚本，例如嵌入的 jsfidle demo，请确保引入 [external-script](zh-cn/plugins.md?id=external-script) 插件。

## ext

- 类型：`String`
- 默认：`'.md'`

请求文件扩展名。

```js
window.$docsify = {
  ext: '.md',
};
```

## externalLinkRel

- 类型：`String`
- 默认：`'noopener'`

默认为 `'noopener'` (no opener) 可以防止新打开的外部页面（当 [externalLinkTarget](#externallinktarget) 设为 `'_blank'` 时）能够控制我们的页面。 如果不是 `'_blank'`，则不会设置 `rel`。 查看[此帖](https://mathiasbynens.github.io/rel-noopener/)获取更多关于你可能想要使用此选项的信息。

```js
window.$docsify = {
  externalLinkRel: '', // default: 'noopener'
};
```

## externalLinkTarget

- 类型：`String`
- 默认：`'_blank'`

在 markdown 中打开外部链接的目标。 默认为 `'_blank'` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  externalLinkTarget: '_self', // default: '_blank'
};
```

## fallbackLanguages

- 类型：`Array<string>`

当页面请求时，如果给定的本地语言不存在，则回退到默认语言的语言列表。

示例：

- 尝试获取 `/de/overview` 页面。 如果该页面存在，就会显示出来。
- 然后尝试获取默认页面 `/overview`（取决于默认语言）。 如果该页面存在，就会显示出来。
- 如果也不存在，显示404页面。

```js
window.$docsify = {
  fallbackLanguages: ['fr', 'de'],
};
```

## fallbackDefaultLanguage

- 类型：`String`
- 默认：`''`

当请求的页面不存在给定的语言时，Docsify 将回退到此选项指定的语言。

例如，在上述情况下，如果 `/de/overview` 不存在，而 `fallbackDefaultLanguage` 被配置为 `zh-cn`，Docsify 将获取 `/zh-cn/overview` 而不是 `/overview`。

```js
window.$docsify = {
  fallbackLanguages: ['fr', 'de'],
  fallbackDefaultLanguage: 'zh-cn', // default: ''
};
```

## formatUpdated

- 类型：`String|Function`

我们可以通过 **{docsify-updated<span>}</span>** 变量显示文档更新日期。 并通过 `formatUpdated` 进行格式化。
参见 https://github.com/lukeed/tinydate#patterns

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

- 类型：`Boolean`
- 默认：`false`

该选项将完全隐藏侧边栏，不会在侧边栏显示任何内容。

```js
window.$docsify = {
  hideSidebar: true,
};
```

## homepage

- 类型：`String`
- 默认：`'README.md'`

文档文件夹中的 `README.md` 将被视为网站的主页，但有时你可能需要将另一个文件作为主页。

```js
window.$docsify = {
  // Change to /home.md
  homepage: 'home.md',

  // Or use the readme in your repo
  homepage:
    'https://raw.githubusercontent.com/docsifyjs/docsify/main/README.md',
};
```

## keyBindings

- 类型：`Boolean|Object`
- 默认：`Object`
  - <kbd>\\</kbd> 切换侧边栏菜单
  - <kbd>/</kbd> 焦点在[搜索](zh-cn/plugins#full-text-search)文本框处。 还支持 <kbd>alt</kbd>&nbsp;/&nbsp;<kbd>ctrl</kbd>&nbsp;+&nbsp;<kbd>k</kbd>。

将组合键绑定到自定义回调函数。

键 `bindings` 定义为用 `+` 分隔的大小写不敏感的字符串值。 修饰符键值包括 `alt`、`ctrl`、`meta` 和 `shift`。 非修饰符键值应与键盘事件的 [key](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key) 或 [code](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code) 值相匹配。

`callback` 函数接收[按键事件](https://developer.mozilla.org/en-US/docs/Web/API/Element/keydown_event)作为参数。

> [!IMPORTANT] 让网站访问者知道你的自定义按键是可用的 ！ 如果绑定与 DOM 元素相关联，可考虑插入一个 `<kbd>` 元素作为视觉提示（如<kbd>alt</kbd>+<kbd>a</kbd>），或添加 [title](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title) 和 [aria-keyshortcuts](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-keyshortcuts) 属性作为悬停/焦点提示。

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

通过将绑定配置设置为 `false`，可以完全或单独禁用按键绑定。

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
- 默认：`false`

如果**true**，则从 Markdown 文件 `_navbar.md` 加载导航栏，否则从指定路径加载。

```js
window.$docsify = {
  // 加载 _navbar.md
  loadNavbar: true,

  // 加载 nav.md
  loadNavbar: 'nav.md',
};
```

## loadSidebar

- 类型：`Boolean|String`
- 默认：`false`

如果**true**，则从 Markdown 文件 `_sidebar.md` 加载侧边栏，否则从指定路径加载。

```js
window.$docsify = {
  // 加载 _sidebar.md
  loadSidebar: true,

  // 加载 summary.md
  loadSidebar: 'summary.md',
};
```

## logo

- 类型：`String`

在侧边栏显示的网站 Logo。 你可以使用 CSS 调整它的大小。

> [!IMPORTANT] 只有同时设置了 `name`，Logo 才会可见。 请参阅 [name](#name) 配置。

```js
window.$docsify = {
  logo: '/_media/icon.svg',
};
```

## markdown

- 类型：`Function`

请参见 [Markdown 配置](zh-cn/markdown.md)。

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

## maxLevel

- 类型：`Number`
- 默认：`6`

内容级别的最大值。

```js
window.$docsify = {
  maxLevel: 4,
};
```

## mergeNavbar

- 类型：`Boolean`
- 默认：`false`

在较小的屏幕上，导航栏将与侧边栏合并。

```js
window.$docsify = {
  mergeNavbar: true,
};
```

## name

- 类型：`Boolean | String`

在侧边栏中显示的网站名称。

```js
window.$docsify = {
  name: 'docsify',
};
```

name 项也可以包含自定义 HTML 代码来方便地定制：

```js
window.$docsify = {
  name: '<span>docsify</span>',
};
```

如果`true`, 网站名称将从文档的 `<title>` 标签中推出。

```js
window.$docsify = {
  name: true,
};
```

如果 `false` 或为空，则不显示名称。

```js
window.$docsify = {
  name: false,
};
```

## nameLink

- 类型：`String`
- 默认： `'window.location.pathname'`

网站 `name` 链接到的 URL。

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

## nativeEmoji

- 类型：`Boolean`
- 默认：`false`

使用 GitHub 风格表情图像或原生表情符号字符来渲染表情符号。

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

`false` 时为 GitHub 样式的图像：

<output data-lang="output">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f604.png" alt="smile">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f973.png" alt="partying_face">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f602.png" alt="joy">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f44d.png" alt="+1">
  <img class="emoji" src="https://github.githubassets.com/images/icons/emoji/unicode/1f44e.png" alt="-1">
</output>

`true` 时为原生表情符号字符的图像：

<output data-lang="output">
  <span class="emoji">😄︎</span>
  <span class="emoji">🥳︎</span>
  <span class="emoji">😂︎</span>
  <span class="emoji">👍︎</span>
  <span class="emoji">👎︎</span>
</output>

要渲染短代码作为文本，请将 `:` 字符替换为 `&colon;` HTML 实体。

```markdown
&colon;100&colon;
```

<output data-lang="output">

&colon;100&colon;

</output>

## noCompileLinks

- 类型：`Array<string>`

有时我们不希望 docsify 处理我们的链接： 参见 [#203](https://github.com/docsifyjs/docsify/issues/203)。 我们可以通过指定字符串数组来跳过某些链接的编译。 每个字符串都会被转换成正则表达式 (`RegExp`)，链接的 _whole_ href 会与之匹配。

```js
window.$docsify = {
  noCompileLinks: ['/foo', '/bar/.*'],
};
```

## noEmoji

- 类型：`Boolean`
- 默认：`false`

禁用表情符号解析，并将所有表情符号短代码显示为文本。

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

要禁用单个短代码的表情符号解析功能，请将 `:` 字符替换为 `&colon;` HTML 实体。

```markdown
:100:

&colon;100&colon;
```

<output data-lang="output">

:100:

&colon;100&colon;

</output>

## notFoundPage

- 类型：`Boolean|String|Object`
- 默认：`false`

显示默认 “404 - Not Found” 消息：

```js
window.$docsify = {
  notFoundPage: false,
};
```

加载 `_404.md` 文件：

```js
window.$docsify = {
  notFoundPage: true,
};
```

加载 404 页面的自定义路径：

```js
window.$docsify = {
  notFoundPage: 'my404.md',
};
```

根据本地化情况加载正确的 404 页面：

```js
window.$docsify = {
  notFoundPage: {
    '/': '_404.md',
    '/de': 'de/_404.md',
  },
};
```

> 注意：配置过 `fallbackLanguages` 选项的页面与 `notFoundPage` 选项冲突。

## onlyCover

- 类型：`Boolean`
- 默认：`false`

只在访问主页时加载封面。

```js
window.$docsify = {
  onlyCover: false,
};
```

## plugins

请参见[插件列表](zh-cn/plugins.md)。

## relativePath

- 类型：`Boolean`
- 默认：`false`

如果该选项设为 **true** ，那么链接会使用相对路径。

例如，目录结构如下：

```text
.
└── docs
    ├── README.md
    ├── guide.md
    └── zh-cn
        ├── README.md
        ├── guide.md
        └── config
            └── example.md
```

如果**启用**了相对路径，当前链接是 `http://domain.com/zh-cn/README` ，对应的链接会解析为：

```text
guide.md              => http://domain.com/zh-cn/guide
config/example.md     => http://domain.com/zh-cn/config/example
../README.md          => http://domain.com/README
/README.md            => http://domain.com/README
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

如果未定义或为空，则不显示 GitHub corner。

## requestHeaders

- 类型：`Object`

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

## routerMode

配置网站路径将使用的 URL 格式。

- 类型：`String`
- 默认：`'hash'`

```js
window.$docsify = {
  routerMode: 'history', // default: 'hash'
};
```

对于静态部署的站点（如 在 GitHub 页面上）基于 hash 的路由设置更简单。 对于可以重写 URL 的网站，基于历史记录的格式更好（特别是对于搜索引擎优化而言，基于哈希值的路由对搜索引擎并不那么友好）。

基于 hash 值的路由选择意味着所有 URL 路径都将在地址栏中以 `/#/` 作为前缀。 这是一种技巧，它允许网站加载 `/index.html`，然后使用 `#` 后面的路径来决定加载哪些 markdown 文件。 例如，一个完整的基于 hash 值的 URL 可以如下所示：`https://example.com/#/path/to/page`。 浏览器将实际加载 `https://example.com`（假设你的静态服务器默认提供`index.html`，大多数服务器都是这样做的），然后 Docsify JavaScript 代码将查看 `/#/...`，并确定要加载和渲染的 markdown 文件。
此外，点击链接时，Docsify 路由器会动态更改 hash 值之后的内容。 无论如何，`location.pathname` 的值仍将是 `/`。 当在浏览器中访问这样的 URL 时，hash 路径的部分 _不会_ 被发送到服务器。

另一方面，基于历史的路由意味着 Docsify JavaScript 将使用 [History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) 来动态更改 URL，而无需使用 `#`。 这意味着，搜索引擎将把所有网址视为“真实”网址，在浏览器中访问网址时，完整路径将被发送到服务器。 例如，URL 可能看起来像 `https://example.com/path/to/page`。 浏览器将尝试直接从服务器加载完整的 URL，而不仅仅是 `https://example.com`。 这样做的好处是这些类型的 URL 对搜索引擎更友好，可以被索引（耶！）。 但缺点是，你的服务器或存放网站文件的地方必须能够处理这些 URL。 各种静态网站托管服务允许配置“重写规则”，这样就可以配置服务器，使其无论访问的路径是什么，都始终发回 `/index.html`。 `location.pathname` 的值将显示 `/path/to/page`，因为实际上已经发送到服务器。

太长不看版：优先使用 `hash` 路由（默认）。 如果你有冒险精神，可以学习如何配置服务器，然后切换到 `history` 模式，以获得更好的体验，URL 中不含 `#`，并进行搜索引擎优化。

> **注意** 如果使用 `routerMode: 'history'`，可能需要添加[`alias`](#alias)，以便无论访问哪个路径，都能加载 `_sidebar.md` 和 `_navbar.md` 文件。
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

## routes

- 类型：`Object`

定义能动态提供内容的 “虚拟” 路由。 路由是预期路径与字符串或函数之间的映射。 如果映射值是字符串，它将被视为 markdown 并进行相应的解析。 如果是函数，则应返回 markdown 内容。

路由函数接收最多三个参数：

1. `route` - 请求的路由路径（例如`/bar/baz`）
2. `matched` - 路由匹配的 [`RegExpMatchArray`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)（例如，对于 `/bar/(.+)`，你会得到 `['/bar/baz', 'baz']`）
3. `next` - 这是一个回调，当路由函数为异步时可以调用

请注意，顺序很重要！ 路由的匹配顺序与你声明路由的顺序相同，这意味着在路由重叠的情况下，你可能希望先列出更具体的路由。

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

除字符串外，路由函数还可以返回一个假值（`null` \ `undefined`），以表示忽略当前请求：

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

最后，如果某个特定路径有真正的 markdown 文件（因此路由不应匹配该文件），可以通过返回一个明确的 `false` 值将其排除在外：

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
- 默认：`'Skip to main content'`

决定是否/如何显示网站的 [skip navigation link](https://webaim.org/techniques/skipnav/)。

```js
// Render skip link for all routes
window.$docsify = {
  skipLink: 'Skip to content',
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

```js
// Use default
window.$docsify = {
  skipLink: true, // "Skip to main content"
};
```

## subMaxLevel

- 类型：`Number`
- 默认：`0`

在自定义侧边栏中添加目录（TOC）。

```js
window.$docsify = {
  subMaxLevel: 2,
};
```

如果你在侧边栏中设置了主页链接，并希望它在访问根网址时显示为活动状态，请确保相应更新侧边栏：

```markdown
- Sidebar
  - [Home](/)
  - [Another page](another.md)
```

参见 [#1131](https://github.com/docsifyjs/docsify/issues/1131)。

## themeColor ⚠️ :id=themecolor

> [!IMPORTANT] 废弃于 v5。 使用 `--theme-color` [主题属性](zh-cn/themes#theme-properties) [自定义](zh-cn/themes#customization) 主题颜色。

- 类型：`String`

自定义主题颜色。

```js
window.$docsify = {
  themeColor: '#3F51B5',
};
```

## topMargin ⚠️ :id=topmargin

> [!IMPORTANT] 废弃于 v5。 在使用粘性导航栏时，使用 `--scroll-padding-top` [主题属性](zh-cn/themes#theme-properties) 指定滚动边距。

- 类型：`Number|String`
- 默认：`0`

在视口顶部添加滚动填充。 当你添加了一个粘性或“固定”元素，并希望自动滚动与元素底部对齐时，该功能非常有用。

```js
window.$docsify = {
  topMargin: 90, // 90, '90px', '2rem', etc.
};
```

## vueComponents

- 类型：`Object`

创建并注册全局 [Vue](https://vuejs.org/guide/essentials/component-basics.html)。 指定组件时，以组件名称为键，以包含 Vue 选项的对象为值。 组件 `data` 在每个实例中都是唯一的，不会在用户导航站点时持续存在。

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

## vueGlobalOptions

- 类型：`Object`

指定全局 Vue 选项，以便与未通过 [vueMounts](#mounting-dom-elements)、[vueComponents](#components) 或 [markdown script](#markdown-script) 明确加载的 Vue 内容一起使用。 对全局 `data` 的更改将持续存在，并在使用全局引用的任何地方得到反映。

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

- 类型：`Object`

指定要挂载为 Vue 实例的 DOM 元素及其相关选项。 挂载元素是使用 [CSS 选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，包含 Vue 选项的对象作为值来指定的。 每次加载新页面时，Docsify 都会在主内容区域挂载第一个匹配元素。 挂载元素 `data` 是每个实例的唯一特性，不会在用户导航站点时持续存在。

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
