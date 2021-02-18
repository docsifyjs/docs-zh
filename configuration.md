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

## el

- 类型：`String`
- 默认值：`#app`

docsify 初始化的挂载元素，可以是一个 CSS 选择器，默认为 `#app` 如果不存在就直接绑定在 `body` 上。

```js
window.$docsify = {
  el: '#app',
};
```

## repo

- 类型：`String`
- 默认值: `null`

配置仓库地址或者 `username/repo` 的字符串，会在页面右上角渲染一个 [GitHub Corner](http://tholman.com/github-corners/) 挂件。

```js
window.$docsify = {
  repo: 'docsifyjs/docsify',
  // or
  repo: 'https://github.com/docsifyjs/docsify/',
};
```

## maxLevel

- 类型：`Number`
- 默认值: `6`

默认情况下会抓取文档中所有标题渲染成目录，可配置最大支持渲染的标题层级。

```js
window.$docsify = {
  maxLevel: 4,
};
```

## loadNavbar

- 类型：`Boolean|String`
- 默认值: `false`

加载自定义导航栏，参考[定制导航栏](zh-cn/custom-navbar.md) 了解用法。设置为 `true` 后会加载 `_navbar.md` 文件，也可以自定义加载的文件名。

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
- 默认值: `false`

加载自定义侧边栏，参考[多页文档](zh-cn/more-pages.md)。设置为 `true` 后会加载 `_sidebar.md` 文件，也可以自定义加载的文件名。

```js
window.$docsify = {
  // 加载 _sidebar.md
  loadSidebar: true,

  // 加载 summary.md
  loadSidebar: 'summary.md',
};
```

## hideSidebar

- 类型 : `Boolean`
- 默认值: `true`

这个选项用来完全隐藏侧边栏，侧边栏的任何内容都不会被渲染。

```js
window.$docsify = {
  hideSidebar: true,
};
```

## subMaxLevel

- 类型：`Number`
- 默认值: `0`

自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

```js
window.$docsify = {
  subMaxLevel: 2,
};
```

## auto2top

- 类型：`Boolean`
- 默认值: `false`

切换页面后是否自动跳转到页面顶部。

```js
window.$docsify = {
  auto2top: true,
};
```

## homepage

- 类型：`String`
- 默认值: `README.md`

设置首页文件加载路径。适合不想将 `README.md` 作为入口文件渲染，或者是文档存放在其他位置的情况使用。

```js
window.$docsify = {
  // 入口文件改为 /home.md
  homepage: 'home.md',

  // 文档和仓库根目录下的 README.md 内容一致
  homepage:
    'https://raw.githubusercontent.com/docsifyjs/docsify/master/README.md',
};
```

## basePath

- 类型：`String`

文档加载的根路径，可以是二级路径或者是其他域名的路径。

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

## relativePath

- 类型: `Boolean`
- 默认值: `false`

如果该选项设为 **true** ，那么链接会使用相对路径。

例如，像这样的目录结构：

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

如果 **启用** 了相对路径，当前链接是 `http://domain.com/zh-cn/README` ，对应的链接会解析为：

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

## coverpage

- 类型：`Boolean|String`
- 默认值: `false`

启用[封面页](zh-cn/cover.md)。开启后是加载 `_coverpage.md` 文件，也可以自定义文件名。

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

## logo

- 类型: `String`

在侧边栏中出现的网站图标，你可以使用`CSS`来更改大小

```js
window.$docsify = {
  logo: '/_media/icon.svg',
};
```

## name

- 类型：`String`

文档标题，会显示在侧边栏顶部。

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

## nameLink

- 类型：`String`
- 默认值：`window.location.pathname`

点击文档标题后跳转的链接地址。

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

## markdown

- 类型: `Object|Function`

参考 [Markdown 配置](zh-cn/markdown.md)。

```js
window.$docsify = {
  // object
  markdown: {
    smartypants: true,
    renderer: {
      link: function() {
        // ...
      },
    },
  },

  // function
  markdown: function(marked, renderer) {
    // ...
    return marked;
  },
};
```

## themeColor

- 类型：`String`

替换主题色。利用 [CSS3 支持变量](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables)的特性，对于老的浏览器有 polyfill 处理。

```js
window.$docsify = {
  themeColor: '#3F51B5'
};
```

## alias

- 类型：`Object`

定义路由别名，可以更自由的定义路由规则。 支持正则。

```js
window.$docsify = {
  alias: {
    '/foo/(.*)': '/bar/$1', // supports regexp
    '/zh-cn/changelog': '/changelog',
    '/changelog':
      'https://raw.githubusercontent.com/docsifyjs/docsify/master/CHANGELOG',
    '/.*/_sidebar.md': '/_sidebar.md', // See #301
  },
};
```

## autoHeader

- 类型：`Boolean`

同时设置 `loadSidebar` 和 `autoHeader` 后，可以根据 `_sidebar.md` 的内容自动为每个页面增加标题。[#78](https://github.com/docsifyjs/docsify/issues/78)

```js
window.$docsify = {
  loadSidebar: true,
  autoHeader: true,
};
```

## executeScript

- 类型：`Boolean`

执行文档里的 script 标签里的脚本，只执行第一个 script ([demo](zh-cn/themes.md))。 如果 Vue 存在，则自动开启。

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

注意如果执行的是一个外链脚本，比如 jsfiddle 的内嵌 demo，请确保引入 [external-script](plugins.md?id=外链脚本-external-script) 插件。

## noEmoji

- 类型: `Boolean`

禁用 emoji 解析。

```js
window.$docsify = {
  noEmoji: true,
};
```

?> 如果该选项设为 `false` ，但是你不想解析一些特别的表情符，[参考这里](https://github.com/docsifyjs/docsify/issues/742#issuecomment-586313143)

## mergeNavbar

- 类型: `Boolean`

小屏设备下合并导航栏到侧边栏。

```js
window.$docsify = {
  mergeNavbar: true,
};
```

## formatUpdated

- 类型: `String|Function`

我们可以通过 **{docsify-updated<span>}</span>** 变量显示文档更新日期. 并且通过 `formatUpdated`配置日期格式。参考 [https://github.com/lukeed/tinydate#patterns](https://github.com/lukeed/tinydate#patterns)

```js
window.$docsify = {
  formatUpdated: '{MM}/{DD} {HH}:{mm}',

  formatUpdated: function(time) {
    // ...

    return time;
  },
};
```

## externalLinkTarget

- 类型: `String`
- 默认: `_blank`

外部链接的打开方式。默认为 `_blank` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  externalLinkTarget: '_self', // default: '_blank'
};
```

## cornerExternalLinkTarget

- 类型:`String`
- 默认值:`_blank`

右上角链接的打开方式。默认为 `_blank` （在新窗口或者标签页中打开）

```js
window.$docsify = {
  cornerExternalLinkTarget: '_self', // default: '_blank'
};
```

## externalLinkRel

- 类型: `String`
- 默认值: `noopener`

默认为 `noopener` (no opener) 可以防止新打开的外部页面（当 [externalLinkTarget](#externallinktarget) 设为 `_blank` 时）能够控制我们的页面，没有设为 `_blank` 的话就不需要设置这个选项了。

```js
window.$docsify = {
  externalLinkRel: '', // default: 'noopener'
};
```

## routerMode

- 类型: `String`
- 默认: `hash`

```js
window.$docsify = {
  routerMode: 'history', // default: 'hash'
};
```

## crossOriginLinks

- type: `Array`

当设置了`routerMode:'history'`时，你可能会面临跨域的问题，参见 [#1379](https://github.com/docsifyjs/docsify/issues/1379) 。在 Markdown 内容中，有一个简单的方法可以解决，参见[helpers](zh-cn/helpers.md) 中的跨域链接。

```js
window.$docsify = {
  crossOriginLinks: ['https://example.com/cross-origin-link'],
};
```

## noCompileLinks

- 类型: `Array`

有时我们不希望 docsify 处理我们的链接。 参考 [#203](https://github.com/docsifyjs/docsify/issues/203)

```js
window.$docsify = {
  noCompileLinks: ['/foo', '/bar/.*'],
};
```

## onlyCover

- 类型: `Boolean`

只在访问主页时加载封面。

```js
window.$docsify = {
  onlyCover: false,
};
```

## requestHeaders

- 类型: `Object`

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

## ext

- 类型: `String`

资源的文件扩展名。

```js
window.$docsify = {
  ext: '.md',
};
```

## fallbackLanguages

- 类型: `Array<string>`

一个语言列表。在浏览这个列表中的语言的翻译文档时都会在请求到一个对应语言的翻译文档，不存在时显示默认语言的同名文档

Example:

- 尝试访问`/de/overview`，如果存在则显示
- 如果不存在则尝试`/overview`（取决于默认语言），如果存在即显示
- 如果也不存在，显示404页面

```js
window.$docsify = {
  fallbackLanguages: ['fr', 'de'],
};
```

## notFoundPage

- 类型: `Boolean` | `String` | `Object`

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

## topMargin

- 类型: `Number`
- 默认值: `0`

让你的内容页在滚动到指定的锚点时，距离页面顶部有一定空间。当你使用 `固定页头` 布局时这个选项很有用，可以让你的锚点对齐标题栏。

```js
window.$docsify = {
  topMargin: 90, // default: 0
};
```

## vueComponents

- type: `Object`

创建并注册全局 [Vue组件](https://vuejs.org/v2/guide/components.html) 。组件是以组件名称为键，以包含 Vue 选项的对象为值来指定的。组件`data`对每个实例都是唯一的，并且在用户浏览网站时不会持久。

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

- type: `Object`

指定 [Vue选项](https://vuejs.org/v2/api/#Options-Data) ，用于未明确使用[vueMounts](#mounting-dom-elements)、[vueComponents](#components)或[markdown脚本](#markdown-script)挂载的 Vue 内容。对全局`data`的更改将持续存在，并在任何使用全局引用的地方得到反映。

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

- type: `Object`

指定要挂载为 [Vue实例](https://vuejs.org/v2/guide/instance.html) 的 DOM 元素及其相关选项。挂载元素使用 [CSS选择器](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) 作为键，并使用包含 Vue 选项的对象作为其值。每次加载新页面时，Docsify 将挂载主内容区域中第一个匹配的元素。挂载元素`data`对每个实例来说都是唯一的，并且不会在用户浏览网站时持久存在。

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
