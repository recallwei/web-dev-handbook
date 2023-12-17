# 初始化

## Docker 配置

```yaml
mongodb:
  container_name: mongodb
  image: mongo
  command: ['mongod', '--auth']
  volumes:
    - mongo_data:/data/db
  restart: always
  ports:
    - 27017:27017
  env_file:
    - .env
```

在默认情况下，MongoDB 是没有开启认证功能的，允许用户以匿名身份登录。  
此处的 `command: ['mongod', '--auth']` 表示开启 MongoDB 的认证功能，用户必须登录才能访问数据库。

## 配置默认用户名和密码

Docker 环境变量中添加 `MONGO_INITDB_ROOT_USERNAME` 和 `MONGO_INITDB_ROOT_PASSWORD`。

## 进入 MongoDB 控制台

通过 Docker 容器进入 MongoDB 控制台。

```bash
docker ps
docker exec -it [CONTAINER_ID] mongosh
```

## 切换至 admin 数据库

默认情况下，MongoDB 会创建一个名为 `admin` 的数据库，该数据库是 MongoDB 的管理数据库，我们可以在该数据库下创建用户，然后再切换至其他数据库。

```mongosh
use admin
```

## 登录初始管理员用户

登录初始管理员用户，用户名和密码就是环境变量中配置的 `MONGO_INITDB_ROOT_USERNAME` 和 `MONGO_INITDB_ROOT_PASSWORD`。

```js
db.auth([MONGO_INITDB_ROOT_USERNAME], [MONGO_INITDB_ROOT_PASSWORD])
```

## 创建用户并赋予数据库权限

创建一个名为 `mongo` 的用户，密码为空，拥有 `test-mongo` 数据库的所有权限。

```js
db.createUser({
  user: 'mongo',
  pwd: '',
  roles: [
    {
      role: 'dbOwner',
      db: 'test-mongo'
    }
  ]
})
```
