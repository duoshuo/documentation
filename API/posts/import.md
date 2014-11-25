### GET `/posts/import.json` 同步评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `posts`* <Map/Array> 评论列表
    - `post_key`* 这条评论在当前站点的 ID
    - `thread_key`* 这条评论所对应文章在当前站点的 ID
    - `message`* 评论内容
