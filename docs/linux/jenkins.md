# Jenkins

## 安装 wget

```bash
sudo dnf install -y wget
```

## 启用 Jenkins 仓库

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

## 安装 Jenkins

```bash
dnf install -y fontconfig java-17-openjdk
dnf install -y jenkins
```

## 启动 Jenkins

```bash
systemctl start jenkins # 启动 Jenkins
systemctl enable jenkins # 设置开机自启
```

## 设置防火墙

默认 Jenkins 服务是在 8080 端口，所以需要开放 8080 端口。

```bash
YOURPORT=8080
PERM="--permanent"
SERV="$PERM --service=jenkins"

firewall-cmd $PERM --new-service=jenkins
firewall-cmd $SERV --set-short="Jenkins ports"
firewall-cmd $SERV --set-description="Jenkins port exceptions"
firewall-cmd $SERV --add-port=$YOURPORT/tcp
firewall-cmd $PERM --add-service=jenkins
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload
```

## 修改 Jenkins 端口

```bash
vi /etc/sysconfig/jenkins
```

添加或修改 `JENKINS_PORT` 为你想要的端口，例如 `9090`。

```bash
JENKINS_PORT="9090"
```

修改完端口后，重启 Jenkins 服务。

```bash
systemctl restart jenkins
```

## 登录 Jenkins

打开浏览器访问 IP + Jenkins 端口号，例如 `http://x.x.x.x:8080`，如果你修改了端口，就输入你修改的端口。

初始化的时候如果修改端口需要设置 Jenkins 实例的 URL，例如 `http://x.x.x.x:9090`。

## 查看初始化后的管理员密码

```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```
