## 多说文档仓库

此文档仓库包括多说 API 文档、插件文档以及适配各个 SDK 的模块文档等文档。

### 接口 Host

多说提供两种不同的接口 Host，分别为，这些接口 Host 提供的接口列表都相同：
- `http://api.duoshuo.com` 更原子化的 API 接口，主要为服务器端通信设计
- `http://duoshuo.com/api` 支持跨域请求，方便前端与客户端发起请求

### 接口列表

此页面列举了所有接口列表与大概的请求字段，如有需要查看请求范例，或阅读返回字段以及错误代码，可以点击到相关接口的详述页面进行阅读。

#### [评论相关接口](./API/posts.md)
- POST `/posts/create.json` 发表评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `message`* <String> 评论内容
  - `thread_key` <String> 被评论文章在原站点的文章标识，如果有 `thread_id` ，此参数是可选参数，否则是必选参数。
  - `thread_id` <String> 被评论文章的多说文章ID，如果有 `thread_key`，此参数是可选参数，否则是必选参数。
  - `parent_id` <String> 父评论（被回复的评论）的 ID
  - `author_name` <String> 作者名字。如果已登陆多说，此参数是可选参数，否则是必选参数。
  - `author_email` <String> 作者邮箱。如果已登陆多说，此参数是可选参数，否则是必选参数。
  - `author_url` <String> 作者网址
  - `remote_auth` <String> `remote_auth` 串是判断用户是否登录的依据。
  - `jwt` <String> 用户身份信息
  - `access_token` <String> SSO 登录获取的 `access_token`
- GET `/posts/import.json` 同步评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `posts`* <Map/Array> 评论列表
    - `post_key`* 这条评论在当前站点的 ID
    - `thread_key`* 这条评论所对应文章在当前站点的 ID
    - `message`* 评论内容
- GET `/log/list.json` 同步评论到本地的通知接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `since_id` <int64> `0` 同步开始的记录 ID
  - `limit` <int> `50` 最大条数，1 ~ 200
  - `order` <String> `desc|asc`

#### [文章相关接口](./API/threads.md)
- GET `/threads/counts.json` 获得当前文章评论数和转发数接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `threads`* <String> 你需要获取的文章的 `thread-key`, 如有多个 `thread-key` 以逗号分割。
- POST `/threads/import.json` 同步文章到多说接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `threads`* <Map/Array> 文章列表
    - `thread_key`* <String> 文章在原站点中的 ID
    - `title`* <String> 文章标题
    - `url`* <String> 文章 URL
- GET `/threads/listPosts.json` 获得当前文章的评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `thread_key`* <String> 当前文章的 `thread-key`
  - `page`* <String>
  - `limit`* <int>
  - `order` <String> `desc|asc` 返回的评论的排序规则

#### [站点相关接口](./API/sites.md)
- GET `/sites/listTopThreads.json` 获取站点中每日/每周/每月/总评论数最多的文章
  - `short_name`* <String> 站点注册的多说二级域名
  - `range` <String> `daily|weekly|monthly|all` 获取的范围
  - `num_items` <int> `5` 获取的条数
  - `channel_key` <int> 文章所属的频道
- POST `/sites/join.json` SSO 单点登录接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `access_token`* <String> SSO 完成时从多说获得的用户 `token`
  - `user`* <Map/Array> 站点创建的用户信息
    - `user_key`* <String> 这个用户在用户站点中的 ID（**注意：**此ID不是用户在多说的ID）
    - `name`* <String> 用户的显示名

#### [用户相关接口](./API/users.md)
- POST `/users/import.json` 同步用户接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `users`* <Map/Array> 用户列表
    - `user_key`* 这个用户在当前站点的 ID
    - `name`* 用户的显示名
- GET `/users/profile.json` 获得用户数据
  - `user_id`* <String> 用户ID

#### 错误代码(./API/errors.md)
  - API 错误代码列表

**TIP**: 接口描述中带 * 号的接口需要鉴权，字段描述中带 * 号的字段是必须提供的字段，字段可选值中默认指是第一位，例如在 `/threads/listPosts.json` 接口中查询字段 `order` 的可选值是 `desc` 或者 `asc`，默认为 `desc`

### 组件文档

多说 embed.js 默认提供一些包装好业务逻辑的组件，这些组件可以很方便的通过 directive 的方式在页面上引用，仅需简单配置，就能完成一系列的功能。

- 最新评论组件
- 最近访客组件
- 热门文章组件
- 文章评论数组件
