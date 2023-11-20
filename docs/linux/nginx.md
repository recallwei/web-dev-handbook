# Nginx

## 安装 Nginx

```bash
dnf install nginx
systemctl start nginx # 启动 Nginx
systemctl enable nginx # 设置开机自启
```

## Nginx 配置文件

### nginx.conf

nginx.conf 是 Nginx 的主配置文件，通常位于 `/etc/nginx/nginx.conf`，包含了全局配置和一些默认的规则。

### /conf.d

/conf.d 是 Nginx 的配置文件目录，通常位于 `/etc/nginx/conf.d`，用于存放特定的配置文件。在该目录下可以创建多个以 .conf 为后缀的配置文件，这样可以将配置逻辑分开，使得配置更加模块化、易于管理。

## 为 Nest API 设置 Nginx

```bash
vi /etc/nginx/conf.d/nest.conf # 编辑 Nginx 配置文件
```

```nginx
server {
 server_name example.com;
  charset 'utf-8';

  location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'Upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Access-Control-Allow-Origin https://xxx,http://localhost:4060; # 跨域配置
  }

  location = /favicon.ico {
    access_log off;
    log_not_found off;
  }
  location = /robots.txt {
    access_log off;
    log_not_found off;
  }
}
```

```bash
nginx -t # 检查配置文件是否正确
systemctl restart nginx # 重启 Nginx
```

## 常见问题

[(13: Permission denied) while connecting to upstream:[nginx]](https://stackoverflow.com/questions/23948527/13-permission-denied-while-connecting-to-upstreamnginx)
