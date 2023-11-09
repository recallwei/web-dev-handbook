# changesets

pnpm workspace + changesets 是一个常见的 monorepo组合，可以让我们更好的管理 monorepo 项目的版本发布。

## 安装

```bash
pnpm add -D @changesets/cli
pnpm changeset init
```

## 创建一个 changeset

```bash
pnpm changeset
```

1. 选择想要发布的包，可以同时选择多个包。
2. 然后选择这些包 changeset 的类型，如 major、minor、patch，对应包更新的类型。
3. 选择完成后，会在根目录下生成一个 `.changeset` 文件夹，里面包含了所有的 changeset。

## 更新包的版本

```bash
pnpm changeset version
```

这个命令会根据 changeset 更新所有包的版本号。

## 发布包

```bash
pnpm changeset publish
```

这个命令会根据 changeset 发布所有包。
