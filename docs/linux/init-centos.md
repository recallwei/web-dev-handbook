# 初始化 CentOS 服务器

以部署一个 Nest.js API 为例，介绍如何初始化 CentOS 服务器。  
本文档适用于 CentOS 8+。

## 安装 dnf 包管理器

CentOS 8 默认会预装 dnf 包管理器，如果没有安装，可以使用以下命令安装：

```bash
yum install -y dnf
dnf --version # 查看版本
```

:::tip{title="提示"}
`-y` 参数表示自动回答 yes，无需手动再次确认。
:::

## dnf 更新包版本

```bash
dnf update
```

## 安装 Git

```bash
dnf install -y git
```

## 安装 Node

```bash
dnf module list nodejs # 查看 Node 可用版本
dnf module enable nodejs:18 # 启用 Node 18
dnf install nodejs # 安装 Node
```

## 安装 n 模块

```bash
npm install -g n
n lts # 安装最新 LTS 版本
node -v # 查看 Node 版本
npm -v # 查看 npm 版本
```

:::warning{title="警告"}
npm 版本可能显示不正确，需要重启机器以更新至相应的版本。
:::

## 安装 pnpm

```bash
npm i -g pnpm
```

## 安装 Docker

```bash
dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
dnf update
dnf install docker-ce docker-ce-cli containerd.io
systemctl start docker # 启动 Docker
systemctl enable docker # 设置 Docker 开机自启
docker --version # 查看 Docker 版本
```

## Docker 中运行 PostgreSQL

```bash
docker run --name postgresql-container -e POSTGRES_PASSWORD=your_password -p 5432:5432 -d postgres # 运行 PostgreSQL
docker ps # 查看正在运行的容器
```

## 运行 Nest API

```bash
pnpm i # 安装依赖
pnpm prisma:migrate:dev # 执行数据库迁移
pnpm dev:pm2 # pm2 运行 Nest API
```

## 安装 Nginx

```bash
dnf install nginx
systemctl start nginx # 启动 Nginx
systemctl enable nginx # 设置 Nginx 开机自启
```
