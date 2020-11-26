# 部署

和 GitBook 生成的文档一样，我们可以直接把文档网站部署到 GitHub Pages 或者 VPS 上。

## GitHub Pages

GitHub Pages 支持从三个地方读取文件

- `docs/` 目录
- master 分支
- gh-pages 分支

我们推荐直接将文档放在 `docs/` 目录下，在设置页面开启 **GitHub Pages** 功能并选择 `master branch /docs folder` 选项。

![github pages](../_images/deploy-github-pages.png)

!> 可以将文档放在根目录下，然后选择 **master 分支** 作为文档目录。你需要在部署位置下放一个 `.nojekyll` 文件（比如 `/docs` 目录或者 gh-pages 分支）

## GitLab Pages

如果你正在部署你的主分支, 在 `.gitlab-ci.yml` 中包含以下脚本：

?> `.public` 的解决方法是这样的，`cp` 不会无限循环的将 `public/` 复制到自身。

```YAML
pages:
  stage: deploy
  script:
  - mkdir .public
  - cp -r * .public
  - mv .public public
  artifacts:
    paths:
    - public
  only:
  - master
```

!> 你可以用 `- cp -r docs/. public` 替换脚本, 如果 `./docs` 是你的 docsify 子文件夹。

## Gitee Pages

在对应的 Gitee 仓库服务中选择 `Gitee Pages`，选择您要部署的分支，填写您要部署的分支上的目录，例如`docs`，填写完成之后点击启动即可。

## Firebase 主机

!> 你需要先使用谷歌账号登陆 [Firebase 控制台](https://console.firebase.google.com) ，然后使用 `npm i -g firebase-tools` 命令安装 Firebase CLI 。

使用命令行浏览到你的 Firebase 项目目录，大致是 `~/Projects/Docs` 等等。在这里执行 `firebase init` 命令，从菜单中选择 `Hosting` （使用 **空格键** 选择， **方向键** 切换选项， **回车键** 确认。遵照安装说明。

然后你会有个 `firebase.json` 文件，内容大致如下（我把部署目录从 `public` 改为 `site` 了）：

```json
{
  "hosting": {
    "public": "site",
    "ignore": ["firebase.json", "**/.*", "**/node_modules/**"]
  }
}
```

完成后，执行 `docsify init ./site` 构建起始模板（将`site`替换为你在运行`firebase init`时确定的部署目录 - 默认情况下为`public`）。 添加/编辑文档，然后在项目根目录执行 `firebase deploy`。

## VPS

和部署所有静态网站一样，只需将服务器的访问根目录设定为 `index.html` 文件。

例如 nginx 的配置

```nginx
server {
  listen 80;
  server_name  your.domain.com;

  location / {
    alias /path/to/dir/of/docs/;
    index index.html;
  }
}
```

## Netlify

1.  登陆你的[Netlify](https://www.netlify.com/)账号
2.  在[dashboard](https://app.netlify.com/)页上点击 **New site from Git**
3.  选择那个你用来存储文档的git仓库，将 **Build Command** 留空, 将 **Publish directory** 区域填入你的`index.html`所在的目录，例如：填入`docs`(如果你的`index.html`的相对路径是`docs/index.html`的话)

### HTML5 路由

当使用HTML5路由时，你需要设置一条将所有请求重定向到你的`index.html`的重定向规则。当你使用Netlify时这相当简单，在你的**Publish Directory**下创建一个`_redirects`文件，写进以下内容就可以了 :tada:

```sh
/* /index.html 200
```

## ZEIT Now

1. 安装 [Now CLI](https://zeit.co/download) ： `npm i -g now`
2. 切换到你的 docsify 网站的文档目录，例如 `cd docs`
3. 用一个指令来部署： `now`

## AWS Amplify

1. 在 Docsify 项目的 `index.html` 中设置 routerMode 为 *history* 模式：

```html
<script>
    window.$docsify = {
      loadSidebar: true,
      routerMode: 'history'
    }
</script>
```

2. 登录到你的 [AWS 控制台](https://aws.amazon.com)。
3. 到 [AWS Amplify 仪表盘](https://aws.amazon.com/amplify)。
4. 选择 **Deploy** 路线来设置你的项目。
5. 若有提示，如果你希望在项目根目录下保存你的文档，保持构建设置为空；如果你想保存文档到其它目录，修改`amplify.yml`:

```yml
version: 0.1
frontend:
  phases:
    build:
      commands:
        - echo "Nothing to build"
  artifacts:
    baseDirectory: /docs
    files:
      - '**/*'
  cache:
    paths: []
```

6. 依次添加如下跳转规则。注意第二条的 PNG 是图片格式，如果你要使用其它图片格式，可以相应修改。

| Source address | Target address | Type          |
|----------------|----------------|---------------|
| /<*>.md        | /<*>.md        | 200 (Rewrite) |
| /<*>.png       | /<*>.png       | 200 (Rewrite) |
| /<*>           | /index.html    | 200 (Rewrite) |

## Docker

- 创建 docsify 的文件

你需要准备好初始文件，而不是在容器中制作。
请参阅 [快速开始](https://docsify.js.org/#/zh-cn/quickstart) 部分，了解如何手动或使用 [docsify-cli](https://github.com/docsifyjs/docsify-cli) 创建这些文件。

```sh
index.html
README.md
```

- 创建 Dockerfile

```Dockerfile
FROM node:latest
LABEL description="A demo Dockerfile for build Docsify."
WORKDIR /docs
RUN npm install -g docsify-cli@latest
EXPOSE 3000/tcp
ENTRYPOINT docsify serve .
```

创建成功后当前的目录结构应该是这样的：

```sh
index.html
README.md
Dockerfile
```

- 构建 docker 镜像

```sh
docker build -f Dockerfile -t docsify/demo .
```

- 运行 docker 镜像

```sh
docker run -itp 3000:3000 --name=docsify -v $(pwd):/docs docsify/demo
```
