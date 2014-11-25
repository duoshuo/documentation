### 用户相关接口

- POST `/users/import.json` 同步用户接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `users`* <Map/Array> 用户列表
    - `user_key`* 这个用户在当前站点的 ID
    - `name`* 用户的显示名
- GET `/users/profile.json` 获得用户数据
  - `user_id`* <String> 用户ID
