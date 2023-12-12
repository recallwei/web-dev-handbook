# 初始化

## 配置默认用户名和密码

Docker 环境变量中添加 `MONGO_INITDB_ROOT_USERNAME` 和 `MONGO_INITDB_ROOT_PASSWORD`。

## 进入 MongoDB 控制台

通过 Docker 容器进入 MongoDB 控制台。

```bash
docker ps
docker exec -it [CONTAINER_ID] bash
```

```bash
mongosh
```

## 切换至 admin 数据库

默认情况下，MongoDB 会创建一个名为 `admin` 的数据库，该数据库是 MongoDB 的管理数据库，我们可以在该数据库下创建用户，然后再切换至其他数据库。

```mongosh
use admin
```

## 登录初始管理员用户

登录初始管理员用户，用户名和密码就是环境变量中配置的 `MONGO_INITDB_ROOT_USERNAME` 和 `MONGO_INITDB_ROOT_PASSWORD`。

```mongosh
db.auth([MONGO_INITDB_ROOT_USERNAME], [MONGO_INITDB_ROOT_PASSWORD])
```

## 创建用户

创建一个名为 `mongo` 的用户，密码为空，拥有 `dolphin-admin-mongo` 数据库的所有权限。

```mongosh
db.createUser({ user: "mongo", pwd: "", roles: [{ role: "dbOwner",db: "dolphin-admin-mongo" }] })
```
