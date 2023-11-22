# 同步多个仓库

有时我们想将本地分支同时推送至多个远程仓库，比如本地仓库同时推送到 GitHub 和 GitLab 上，这通常用于代码备份。

## 查看远程仓库

首先，我们可以使用 `git remote -v` 命令来查看当前关联的远程仓库：

```bash
git remote -v
```

## 添加远程仓库

然后，我们可以使用 `git remote add` 命令来添加新的远程仓库：

```bash
git remote add <new-origin> <remote-url>
git remote -v
```

`new-origin` 为新的远程仓库在本地的关联别名，将 `remote-url` 替换为新的远程仓库的 Git 地址。

## 推送至远程仓库

### 推送至远程仓库指定分支

```bash
git push <remote-name> HEAD:<branch-name>
```

此处 HEAD 为当前最新提交。

### 强制推送

如果远程仓库与本地仓库的提交历史不一致，可以使用 `--force` 参数强制推送：

```bash
git push <remote-name> HEAD:<branch-name> --force
```

注意：强制推送会覆盖远程仓库的提交历史，请谨慎使用！
