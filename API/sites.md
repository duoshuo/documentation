### 站点相关接口

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
