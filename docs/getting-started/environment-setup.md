---
title: 环境准备
sidebar_position: 3
---

# 环境准备

适用对象：第一次在本地或团队环境中启动潮汐栈的读者。

## 最小准备项

- 一台能够运行 Docker 的机器
- 可访问镜像源和相关依赖的网络环境
- 浏览器和基础命令行能力
- 如果要运行开发平台，需确保本机或目标主机允许访问 Docker Engine API

## 先判断你属于哪种场景

### 本地体验

适合：

- 个人试用
- 功能演示
- 快速验证一个简单业务流程

推荐方式：

- 优先使用 Docker Desktop
- 按照 [安装开发平台](./install-develop-platform) 的 compose 路径快速启动

### 团队环境

适合：

- 多人协作
- 长期联调
- 需要稳定的数据、消息队列和持久化目录

推荐方式：

- 使用 Docker Engine
- 结合 [运维管理](../operations/) 规划依赖、端口、存储与升级方式

## Docker 安装建议

### Docker Desktop

适合本地体验环境，优点是安装和管理都更简单。Mac、Windows 和 Linux 桌面环境都可以优先选择 Docker Desktop。

### Docker Engine

适合团队开发服务器或不需要图形界面的环境。常见 Linux 服务器安装后，还需要额外确认：

- Docker 服务能够正常启动
- 当前用户具有执行 Docker 命令的权限
- 目标机器网络策略允许开发平台访问所需端口

## 配置 Docker Engine API

潮汐栈开发平台需要调用 Docker Engine API 来管理调试实例。默认情况下 Docker 不会开放远程网络访问，因此需要手动开启。

使用当前推荐的 compose 安装方式时，开发平台容器会通过 `host.docker.internal:2375` 访问宿主机 Docker API，因此宿主机仍然需要先把这条访问链路准备好。

:::warning
`2375` 端口默认不带 TLS，建议只在本机回环地址或可信内网中暴露，不要直接向公网开放。
:::

### Mac

Docker Desktop 常见做法是通过 `socat` 把本地 `docker.sock` 映射到 `127.0.0.1:2375`：

```bash
docker run -d \
  --name docker-api \
  --restart always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 127.0.0.1:2375:2375 \
  alpine/socat \
  TCP-LISTEN:2375,fork \
  UNIX-CONNECT:/var/run/docker.sock
```

### Windows

在 Docker Desktop 设置中开启 `Expose daemon on tcp://localhost:2375 without TLS`。

如果后续启动开发平台时仍然无法连接 Docker API，可以再尝试补充端口代理：

```bash
netsh interface portproxy add v4tov4 listenport=2375 connectaddress=127.0.0.1 connectport=2375 listenaddress= protocol=tcp
```

### Linux

常见做法是修改 Docker 的 `systemd` 启动参数，为 `ExecStart` 增加 `-H tcp://172.17.0.1:2375`，然后重新加载并重启 Docker：

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

如果你的 Docker 网桥地址不是 `172.17.0.1`，需要按实际环境调整。

## 验证 Docker API 是否可用

配置完成后，执行：

```bash
curl http://localhost:2375
```

如果返回类似 `{"message":"page not found"}`，通常说明 API 已经可访问。

## 下一步

环境准备完成后，继续看 [安装开发平台](./install-develop-platform)。

如果你准备的是团队共享环境或长期运行环境，继续看 [安装与初始化](../operations/installation-and-initialization)。
