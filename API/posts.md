### 评论相关接口

#### POST `/posts/create.json` 发表评论接口
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

#### GET `/posts/import.json` 同步评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `posts`* <Map/Array> 评论列表
    - `post_key`* 这条评论在当前站点的 ID
    - `thread_key`* 这条评论所对应文章在当前站点的 ID
    - `message`* 评论内容
    
#### GET `/log/list.json` 同步评论到本地的通知接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `since_id` <int64> `0` 同步开始的记录 ID
  - `limit` <int> `50` 最大条数，1 ~ 200
  - `order` <String> `desc|asc`
