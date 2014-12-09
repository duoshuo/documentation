## 多说 API 接口文档

此文档仓库包括多说 API 文档、插件文档以及适配各个 SDK 的模块文档等文档。

### 接口 Host

多说提供两种不同的接口 Host，分别为，这些接口 Host 提供的接口列表都相同：
- `http://api.duoshuo.com` 更原子化的 API 接口，主要为服务器端通信设计
- `http://duoshuo.com/api` 支持跨域请求，方便前端与客户端发起请求

### 接口列表

此页面列举了所有接口列表与大概的请求字段，如有需要查看请求范例，或阅读返回字段以及错误代码，可以点击到相关接口的详述页面进行阅读。

#### 评论相关接口
- POST `/posts/create.json` 发表评论接口
- GET `/posts/import.json` 同步评论接口
- GET `/log/list.json` 同步评论到本地的通知接口

#### 文章相关接口
- GET `/threads/counts.json` 获得当前文章评论数和转发数接口
- POST `/threads/import.json` 同步文章到多说接口
- GET `/threads/listPosts.json` 获得当前文章的评论接口

#### 站点相关接口
- GET `/sites/listTopThreads.json` 获取站点中每日/每周/每月/总评论数最多的文章
- POST `/sites/join.json` SSO 单点登录接口

#### 用户相关接口
- POST `/users/import.json` 同步用户接口
- GET `/users/profile.json` 获得用户数据

#### 错误代码
- [API 错误代码列表](API/errors.md)

### 组件文档

多说 embed.js 默认提供一些包装好业务逻辑的组件，这些组件可以很方便的通过 directive 的方式在页面上引用，仅需简单配置，就能完成一系列的功能。

- 最新评论组件
- 最近访客组件
- 热门文章组件
- 文章评论数组件

**TIP**: 接口描述中带 `*` 号的接口**需要鉴权**，字段描述中带 `*` 号的字段是**必须提供的字段**，字段可选值中默认指是第一位，例如在 `/threads/listPosts.json` 接口中查询字段 `order` 的可选值是 `desc` 或者 `asc`，默认为 `desc`
