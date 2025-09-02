# 部署

与 [GitBook](https://www.gitbook.com) 类似，你可以将文件部署到 GitHub Pages、GitLab Pages或 VPS 上。

## GitHub Pages

GitHub Pages 支持从三个地方读取文件：

- `docs/` 目录
- master 分支
- gh-pages 分支

建议将文件保存到仓库 `main` 分支的 `./docs` 子文件夹中。 在设置页面开启 **GitHub Pages** 功能并选择 `main branch /docs folder` 选项。

![GitHub Pages](../_images/deploy-github-pages.png)

> [!IMPORTANT] 你也可以在根目录中保存文件并选择 `main branch` 。
> 你需要在部署位置下放一个 `.nojekyll` 文件（比如 `/docs` 目录或者 gh-pages 分支）

## GitLab Pages

如果你正在部署你的主分支, 在 `.gitlab-ci.yml` 中包含以下脚本：

> [!TIP]  `.public` 的解决方法是这样的，`cp` 不会无限循环的将 `public/` 复制到自身。

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

> !IMPORTANT] 你可以用 `- cp -r docs/. public` 替换脚本，如果 `./docs` 是你的 docsify 子文件夹。

## Firebase 主机

> [!IMPORTANT] 你需要先使用谷歌账号登录 [Firebase 控制台](https://console.firebase.google.com)，然后使用 `npm i -g firebase-tools` 命令安装 Firebase CLI 。

使用终端，确定并导航到你的 Firebase 项目目录。 这可能是 `~/Projects/Docs`，等等。 在这里执行 `firebase init` 命令，从菜单中选择 `Hosting`（使用**空格键**选择，**方向键**切换选项，**回车键**确认）。 遵照安装说明。

你的 `firebase.json` 文件应该与此相似（我将部署目录从 `public` 改为了 `site`）：

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

使用以下 nginx 配置。

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

1. 登录你的[Netlify](https://www.netlify.com/)账号。
2. 在 [dashboard](https://app.netlify.com/) 页面，单击 **Add New Site**。
3. 选择 GitHub。
4. 选择存放文档的存储库，在**Base Directory**中添加存放文件的子文件夹。 例如，应为 `docs`。
5. 在**Build Command**区域留空。
6. 在**Publish directory**区域，如果你在**Base Directory**中添加了 `docs`，你会看到 Publish directory 中填充了 `docs/`
7. Netlify 很聪明，会在 `docs/` 文件夹中查找 `index.html` 文件。

### HTML5 路由

当使用 HTML5 路由时，你需要设置一条将所有请求重定向到你的 `index.html` 的重定向规则。 当你使用Netlify时这相当简单。 只需在 docs 目录中创建一个名为 `_redirects` 的文件，并将此代码段添加到文件中，就可以了：

```sh
/*    /index.html   200
```

## Vercel

1. 安装 [Vercel CLI](https://vercel.com/download) ： `npm i -g vercel`
2. 切换到你的 docsify 网站的文档目录，例如 `cd docs`
3. 用一个指令来部署： `vercel`

## AWS Amplify

1. 在 Docsify 项目的 `index.html` 中设置 routerMode 为 _history_ 模式。

```html
<script>
  window.$docsify = {
    loadSidebar: true,
    routerMode: 'history',
  };
</script>
```

2. 登录到你的 [AWS 控制台](https://aws.amazon.com)。
3. 到 [AWS Amplify 仪表盘](https://aws.amazon.com/amplify)。
4. 选择 **Deploy** 路径来设置你的项目。
5. 若有提示，如果你希望在项目根目录下保存你的文档，保持构建设置为空。 如果你从不同目录提供文档，请自定义你的 amplify.yml

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

6. 在其显示的顺序中添加以下重定向规则。 请注意，第二项记录是一个 PNG 图像，您可以在其中使用任何图像格式来更改它。

| Source address                                     | Target address                                     | Type                             |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------- |
| /<\*>.md  | /<\*>.md  | 200 (Rewrite) |
| /<\*>.png | /<\*>.png | 200 (Rewrite) |
| /<\*>                     | /index.html                        | 200 (Rewrite) |

## Stormkit

1. 登录到你的 [Stormkit](https://www.stormkit.io) 帐户。
2. 使用用户界面，从支持 Git 提供商中(GitHub 、GitLab或 Bitbucket) 导入你的文档项目。
3. 前往 Stormkit 中的项目生产环境或在需要时创建一个新环境。
4. 在你的 Stormkit 配置中验证构建命令。 默认情况下，Stormkit CI 将运行 `npm run build` 但你可以在此页面上指定一个自定义构建命令。
5. 将输出文件夹设置为 `docs`
6. 点击“立即部署”按钮来部署你的站点。

在 [Stormkit Documentation](https://stormkit.io/docs) 中阅读更多内容。

## Docker

- 创建 docsify 的文件

  你需要准备初始文件，而不是将其设在容器内。
  请参阅 [快速开始](zh-cn/quickstart) 部分，了解如何手动或使用 [docsify-cli](https://github.com/docsifyjs/docsify-cli) 创建这些文件。

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

## Kinsta 静态网站托管

你可以将 **Docsify** 作为静态网站部署到 [Kinsta](https://kinsta.com/static-site-hosting/) 上。

1. 登录或创建账户以查看你的 [MyKinsta](https://my.kinsta.com/) 面板。

2. 通过 Git 提供商授权 Kinsta。

3. 从左侧边栏选择**Static Sites**，然后按**Add sites**。

4. 选择要部署的版本库和分支。

5. 在构建设置过程中，Kinsta 会自动尝试填写**Build command**、**Node version** 和 **Publish directory**。 如果不会，请填写以下内容：

   - Build command：留空
   - Node version：保留默认选择或特定版本（如 `18.16.0`）
   - Publish directory：`docs`

6. 点击**Create site**。
