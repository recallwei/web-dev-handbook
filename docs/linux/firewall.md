# 防火墙

## 安装防火墙

```bash
dnf install firewalld
```

## 显示防火墙状态

```bash
firewall-cmd --state
```

正常情况下，没有启动会显示 `not running`，启动后会显示 `running`。

## 启动防火墙

```bash
systemctl start firewalld # 启动防火墙
systemctl enable firewalld # 设置防火墙开机启动
systemctl reload firewalld # 重新加载防火墙配置
```

## 查看开放的端口

```bash
firewall-cmd --list-ports
```

## 查看开放的服务

```bash
firewall-cmd --list-services
```

## 查看详细的防火墙规则

```bash
firewall-cmd --list-all
```

## 永久开放端口

```bash
firewall-cmd --permanent --add-port=<PORT_NUMBER>/tcp
firewall-cmd --reload # 重新加载防火墙配置
firewall-cmd --list-ports # 查看开放的端口，验证是否成功
```

```bash
firewall-cmd --permanent --zone=public --add-port=<PORT_NUMBER>/tcp # 指定区域开放端口
```

## 停止防火墙

```bash
systemctl stop firewalld
firewall-cmd --state # 验证是否停止
```

## 禁用防火墙

```bash
systemctl disable firewalld
```
