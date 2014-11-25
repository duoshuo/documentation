### 文章相关接口

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
