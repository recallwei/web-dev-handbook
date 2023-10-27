# FAQ

## SSH 连接会话自动关闭

SSH 会话在某些情况下可能会自动断开，防火墙可能会关闭长时间空闲的连接，在你的本机修改 `~/.ssh/config` 文件，添加以下内容：

```bash
vim ~/.ssh/config
```

```txt
Host *
    ServerAliveInterval 240
```
