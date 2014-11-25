### POST `/threads/import.json` 同步文章到多说接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `threads`* <Map/Array> 文章列表
    - `thread_key`* <String> 文章在原站点中的 ID
    - `title`* <String> 文章标题
    - `url`* <String> 文章 URL
