### GET `/log/list.json` 同步评论到本地的通知接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `since_id` <int64> `0` 同步开始的记录 ID
  - `limit` <int> `50` 最大条数，1 ~ 200
  - `order` <String> `desc|asc`
