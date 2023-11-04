# 常用命令

## 查看容器列表

```bash
docker ps
```

## 查看镜像列表

```bash
docker images
```

```bash
docker image ls
```

## 构建镜像

```bash
docker build -t <IMAGE_NAME> .
```

## 拉取镜像

```bash
docker pull <IMAGE_NAME>
```

## 删除容器

```bash
docker rm <CONTAINER_NAME>
```

## 删除镜像

```bash
docker rmi <IMAGE_NAME>
```

## 创建前端 SPA 项目的镜像

```bash
FROM node:lts-slim
COPY . /app
WORKDIR /app
RUN npm install -g pnpm
RUN pnpm install
EXPOSE 5173
CMD ["pnpm", "dev"]
```
