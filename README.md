# 开发文档

本文档使用 [Docusaurus 3](https://docusaurus.io/) 搭建。

环境要求：

- Node.js >= 18

> 建议 MacOS/Linux 用户使用 [nvm](https://github.com/nvm-sh/nvm) 管理 node 环境，Windows 用户可考虑使用 [NVM for Windows](https://github.com/coreybutler/nvm-windows) 管理 node 环境

### 安装

```bash
$ yarn
```

### 开发

```bash
$ yarn start
```

该命令将启动一个本地 Web 服务器，展示文档的效果。

### 构建

```bash
$ yarn build
```

该命令将会把文档内容构建成静态文件，并输出到 `build` 目录下，支持部署到任意静态文件 Web 服务器。

### 部署到 Github

推荐使用 GitHub Pages Actions 自动部署。

仓库推送后，GitHub 会自动构建并发布到 Pages。

本地预览构建结果：

```bash
$ yarn build
$ yarn serve
```

使用 SSH:

```bash
$ USE_SSH=true yarn deploy
```

不使用 SSH （使用 HTTPS 方式认证）:

```bash
$ GIT_USER=<Your GitHub username> yarn deploy
```

若使用 Github 的 pages 服务，可以用上述命令将构建后的文档推送到 `gh-pages` 分支.
