# EduV6-dockerConfig
针对国内许多高校鼓励IPv6的 **“校外IPv6资源免计费政策”** 提供校内免流上网的方案

![某高校网信办计费政策](.\img\某高校网信办计费政策.png)

本方案可在校园内网搭建代理服务器，转发至校外服务器代理上网

<img src=".\img\Architecture.png" alt="Architecture" style="zoom: 67%;" />

### 快速启动

[^注]: 出于习惯，此处一律推荐Docker启动，因此P1、P2上都需要安装Docker

需要有一台运行在内网的服务器或是电脑（我用的是一台GMK的mini主机）作为代理服务器以下称为P1，确保支持IPv6

还需要一台运行在校外的服务器，常见方案是VPS（我用的轻量级的腾讯云主机），以下称为P2，确保有公网的IPv6

在此架构中P2作为服务端，P1作为客户端。

#### P1

```shell
git clone https://github.com/gitleaks/gitleaks.git#克隆配置仓库

docker pull ghcr.io/yuha0lin/v2ray:latest#拉取EduV6镜像

修改client-config.json文件，填写id以及P2的ip地址

docker compose docker-compose.client.yml up -d#启动EduV6
```

#### P2

```shell
git clone https://github.com/gitleaks/gitleaks.git#克隆配置仓库

docker pull ghcr.io/yuha0lin/v2ray:latest#拉取EduV6镜像

配置server-config.json文件，配置id

docker compose docker-compose.server.yml up -d#启动EduV6
```

