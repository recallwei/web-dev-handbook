# Verdaccio

## 安装

### 包管理器

使用 npm：

```bash
npm install -g verdaccio
```

使用 yarn：

```bash
yarn global add verdaccio
```

使用 pnpm：

```bash
pnpm add -g verdaccio
```

### Docker

```bash
docker pull verdaccio/verdaccio
docker run -it --rm --name verdaccio -p 4873:4873 verdaccio/verdaccio
```

通过守护进程运行，添加 `-d` 参数：

```bash
docker run -it -d --rm --name verdaccio -p 4873:4873 verdaccio/verdaccio
```

## CLI

进入 Verdaccio 命令行：

```bash
verdaccio
```

## 设置代理

### 全局设置代理

使用 npm：

```bash
npm set registry http://localhost:4873
```

使用 yarn：

```bash
yarn config set registry http://localhost:4873
```

使用 pnpm：

```bash
pnpm config set registry http://localhost:4873
```

### 指定库设置代理

使用 npm：

```bash
npm install lodash --registry http://localhost:4873
```

使用 yarn：

```bash
yarn add lodash --registry http://localhost:4873
```

使用 pnpm：

```bash
pnpm add lodash --registry http://localhost:4873
```

### 使用 .npmrc 设置代理

全局设置代理：

```bash title=".npmrc"
registry=http://localhost:4873
```

指定域设置代理：

```bash title=".npmrc"
@domain:registry=http://localhost:4873
```

### 使用 .yarnrc 设置代理

```bash title=".yarnrc"
registry "http://localhost:4873"
```

## 创建用户

```bash
npm adduser --registry http://localhost:4873
```

## 登录私服

```bash
npm login --registry http://localhost:4873
```

## 发布包至私服

```json title="package.json"
{
  "publishConfig": {
    "registry": "http://localhost:4873"
  }
}
```

使用 `npm publish` 发布包至私服：

```bash
npm publish
```
