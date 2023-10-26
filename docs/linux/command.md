# 常用命令

## 查看端口占用

```bash
lsof -i:pid # pid 为端口号
```

## 强制终止进程

```bash
kill -9 pid # pid 为进程号
kill -9 node # 强制终止 node 进程
```
