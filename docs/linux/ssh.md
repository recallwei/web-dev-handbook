# SSH

## 使用 SSH 进行无密码连接

### 确保 SSH 服务器正在运行

在远程服务器上执行以下命令，确保 SSH 服务器正在运行：

```bash
sudo systemctl status sshd
```

### 生成私钥和公钥

在本地计算机上执行以下命令，生成私钥和公钥：

```bash
ssh-keygen
```

按 Enter 键三次，跳过所有提示，命令完成将生成公钥文件 `~/.ssh/id_rsa.pub` 和私钥文件 `~/.ssh/id_rsa`。

### 将公钥复制到远程服务器

在本地计算机上执行以下命令，将公钥复制到远程服务器：

```bash
ssh-copy-id remote_username@remote_server_ip_address
```

### 测试无密码连接

在本地计算机上执行以下命令，测试无密码连接：

```bash
ssh remote_username@remote_server_ip_address
```

至此，无密码连接配置完成。
