# certbot

certbot 是一个免费的证书申请工具，可以用来申请 let's encrypt 的免费证书。

## 安装

### 通过 snap 安装

详细安装过程参考 [certbot 安装文档](https://certbot.eff.org/instructions?ws=nginx&os=centosrhel8)。

### 通过 Linux 包管理器安装

```bash
dnf install -y epel-release
dnf install -y certbot python3-certbot-nginx
```

## 申请证书

### 交互式命令行申请

```bash
certbot --nginx
```

### 申请并配置证书

```bash
certbot --nginx -d example.com -d www.example.com
```

### 仅申请证书

```bash
certbot certonly --nginx -d example.com -d www.example.com
```

## 证书续期

```bash
certbot renew
```
