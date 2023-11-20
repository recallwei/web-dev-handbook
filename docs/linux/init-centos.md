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
dnf update -y
```

## 安装 Git

```bash
dnf install -y git
```

## 安装 Node

```bash
dnf module list nodejs # 查看 Node 可用版本
dnf module enable nodejs:18 # 启用 Node 18
dnf install -y nodejs # 安装 Node
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
dnf install -y docker-ce docker-ce-cli containerd.io
systemctl start docker # 启动 Docker
systemctl enable docker # 设置开机自启
docker --version # 查看版本
```

## Docker 中运行 PostgreSQL

```bash
docker run --name postgresql-container -e POSTGRES_PASSWORD=your_password -p 5432:5432 -d postgres # 运行 PostgreSQL
docker ps # 查看正在运行的容器
```

## 安装 Docker Compose

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version # 查看版本
```

## 解决 Docker 网络配置问题

清除 Docker 网络配置，然后重新运行 Docker。

```bash
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -t nat -A POSTROUTING -s 172.17.0.0/16 ! -o docker0 -j MASQUERADE
```
