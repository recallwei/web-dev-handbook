# Tanstack Query

## 为什么需要使用 Tanstack Query

随着代码量、项目规模的增长，项目会遇到越来越多的问题，比如：

- UI 层代码和数据层代码耦合严重
- 大量重复代码，需求变动时容易忘记更改
- 组件中充斥着 API 代码，可读性变差

## 将 API 层与 UI 层耦合的问题

UI 组件不需要知道：

- Tanstack Query 对接口状态的管理及其缓存配置
- Axios 及其请求配置
- 接口 URL
- 认证 Header

如果需要将某些、某个接口从 v2 升级为 v3，不应该去修改每一个调用该接口的组件，所以不需要改动 UI 代码。

## Tanstack Query 能带来什么

- 更易实现分页响应
- 提前获取下一页的数据(预加载)
- 乐观更新

## 如何将代码重构为分离的 API 层

1. 提出 Tanstack Query Hooks
2. 重用通用的接口逻辑
3. 使用 Axios 实例和 Tanstack Query 实例
